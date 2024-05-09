---
date: 2024-05-09T18:04:39+02:00
title: "C# 12 Primary Constructors"
slug: csharp-primary-constructors
tags: ["speaking", "csharp", "dotnet"]
cover:
    image: images/abp-dotnetconf-2024.jpg
---
I wrapped up my C# 12 session at the [ABP Dotnet Conference 2024](https://abp.io/conference/2024), and I wanted to share the take-home points, at least about the most relevant features in this language version. Posting the slides made no sense as they were minimal; all the content was packed in the live demo. 

In a follow-up post, I plan to address Collection Expressions and maybe "type any aliases"; this is about Primary Constructors.

- We can now add a list of parameters to a struct or class declaration. This way, we avoid writing an explicit constructor method, sparing us some boilerplate code.

- What I refer to as 'Primary parameters' are unique in that they are in scope throughout the type definition; this means they can be used anywhere within the type.


```cs
public readonly struct Distance(double dx, double dy)
{
    public readonly double Magnitude { get; } = Math.Sqrt(dx * dx + dy * dy);
    public readonly double Direction { get; } = Math.Atan2(dy, dx);
    public override string ToString() => $"{nameof(Magnitude)}: {Magnitude}, {nameof(Direction)}: {Direction}";
    public double Dx { get; } = dx;
    public double Dy { get; } = dy;
}
```

- It's important to note that primary constructor parameters are not class members; therefore, `this.` cannot be used on them. They can be considered static values, but unlike typical static values, they can also be used in non-static methods, offering a unique advantage (some black magic happens behind the scenes.)

- We no longer need to define and assign a type-level field; the compiler will do that behind the scenes when needed; if a behind-the-scenes backing field is unnecessary, it won't be created.

- Primary constructor parameters don't become properties and are inaccessible outside the instance. We can create properties to expose their values if needed. Record types are an exception. Constructor parameters become properties with records, and it makes sense because records are generally used as DTOs, whereas we want the option with class and structs.

- Secondary and parameterless constructors can be added to a primary constructor. They must invoke the primary, passing its values along.

```cs
public Distance() : this(0, 0) { }
```

- With primary constructors, we do not have a method body; how do we handle argument validation? One pattern is to perform validation at property assignation.

```cs
public string AccountID { get; } = ValidAccountNumber(accountID)
    ? accountID
    : throw new ArgumentException("Invalid account number", nameof(accountID));

public static bool ValidAccountNumber(string accountID) => accountID?.Length == 10 && accountID.All(c => char.IsDigit(c));
```

- I like this pattern because it brings property declaration and validation close to each other, making it easier to process and reason about the domain logic. When we perform argument validation in an old-style constructor method, we tend to separate validation and declaration, making it difficult to reconcile the two aspects, especially when we have hundreds of lines between constructor code and property declaration.

- Derived types can have a primary constructor, too; it must invoke the base class' primary constructor.

```cs
public class CheckingAccount(string accountID, string owner, decimal overdraftLimit = 0) : BankAccount(accountID, owner)
```

- Old-style derived types can still derive from a primary constructor type; a regular constructor will invoke the base primary, as we've always been doing.

- Regarding inheritance, we can mix and match primary constructor types with old-style types, making it easy to refactor our libraries to use primary constructors. We know that adopters will have no problem deriving from our refactored types.

- Watch out for "nested captures" of primary parameter values in derived types. If both the derived and the base type capture them, and one (or both) change their captured values, we may end up with non-aligned instance values. Roslyn's analyzer will raise a warning so we can fix our code or mute the alert with a pragma.

- Visual Studio and Visual Studio code offer built-in support for primary constructors (refactorings, etc.) That's true for JetBrains Rider or any other IDEs leveraging Roslyn.

- The primary constructor's original implementation dates back to C# 6 in 2015. It was publicly available in one of those version previews for a short period. Then, it was taken back to the drawing board, only to resurface with record types in C# 9 (?) and custom types in C# 12.
