---
date: 2024-05-10T17:39:02+02:00
title: C# 12 Collection Expressions 
slug: csharp-collection-expressions
tags: ["speaking", "csharp", "dotnet"]
---
This is a follow-up post to [C# 12 Primary
Constructors](/csharp-primary-constructors). Like that article, this one
originates from the preparation notes for my presentation at the [ABP Dotnet
Conference 2024](https://abp.io/conference/2024).

- I love collection expressions. Like primary constructors, collection
expressions will see a significant adoption in the long run.

- Collection expressions introduce a new way to initialize common collection
values in a terse, unified syntax. 

- This is how we initialize collections today: 

```cs
var x1 = new int[] { 1, 2, 3, 4 };
var x2 = Array.Empty<int>();
WriteByteArray(new[] { (byte)1, (byte)2, (byte)3 });
List<int> x3 = new() { 1, 2, 3, 4 };
Span<DateTime> dates = stackalloc DateTime[] { GetDate(0), GetDate(1) };
WriteByteSpan(stackalloc[] { (byte)1, (byte)2, (byte)3 });
```

Notice how the code is diverse depending on the type and the context. It is also
verbose. Look at how we initialize an empty `int` array (second line); it's
lengthy and starkly contrasts with the previous line, where we initialize the
same type with some actual values.  In many situations, casting is needed;
again, take a look at the `WriteByteArray` and `WriteByteSpan` calls.

- With collection expressions, it becomes like this:

```cs
int[] x4 = [1, 2, 3, 4];
int[] x5 = [];
WriteByteArray([1, 2, 3]);
List<int> x6 = [1, 2, 3, 4];
Span<DateTime> dates1 = [GetDate(0), GetDate(1)];
WriteByteSpan([1, 2, 3]);
```

We enclose items within square brackets, and that's all. An empty collection is
empty brackets. We can, of course, call functions or use variables.

- In many scenarios, the compiler will perform several optimizations. It can
allocate the correct capacity or avoid copying data when unnecessary. The
compiler can do that because the supported collection types are well-known and
have been for a long time. We get these performance boosts for free when we switch to
collection expressions.

- Let's look at that `WriteByteArray` call. Let's say that at some
point, maybe months or years after it's been used in many places, we decide to
refactor the method and change the argument type from `byte[]` to `int[].` We'd
have to refactor the old-style caller to eliminate the casting, which is now an
error. We don't need to do any fix with collection expressions as they come with
enhanced inference that will resolve the casting for us.

- On the first line, we're initializing a new array (we aren't calling a method
with a signature), so with collection expressions, if we try to use `var,` it
won't work. In that case, we need to be explicit about the type.

- The spread operator allows us to insert variables and constants and to sort of
"unroll" another collection within the new one, and it does so with optimal
performance. 
```cs
int[] numbers1 = [1, 2, 3];
int[] numbers2 = [4, 5, 6];
int[] moreNumbers = [.. numbers1, .. numbers2, 7, 8, 9];

foreach(var number in moreNumbers)
    Console.WriteLine(number);
```

It would be nice if lambdas were allowed in collection expressions,
like in other languages (Python), but that's not yet an option.

- What about custom collections? But let's imagine I have built a `LineBuffer`
class that inherits from `IEnumrable<chrar>`; it offers some custom features
over its base class. I get an error if I try to use collection expression syntax
on it. It is not a common .NET type, and the compiler doesn't know how to go
around it. 

```cs
public class LineBuffer : IEnumerable<char>
{
    private readonly char[] _buffer = new char[80];

    public LineBuffer(ReadOnlySpan<char> buffer)
    {
        int number = (_buffer.Length < buffer.Length) ? _buffer.Length : buffer.Length;
        for (int i = 0; i < number; i++)
            _buffer[i] = buffer[i];
    }

    public IEnumerator<char> GetEnumerator() => _buffer.AsEnumerable<char>().GetEnumerator();
    IEnumerator IEnumerable.GetEnumerator() => _buffer.GetEnumerator();

    // etc
}

// this causes a compile error
LineBuffer line = ['H', 'e', 'l', 'l', 'o', ' ', 'W', 'o', 'r', 'l', 'd', '!'];
```

- We can support collection expressions in our custom types, though. It's a
two-step process. First, we implement a builder method, then decorate the class
(or struct) with a `CollectionBuilderAttribute.` The attribute maps our type to
the builder method. 

```cs
[CollectionBuilder(typeof(LineBuffer), nameof(Create))]
public class LineBuffer : IEnumerable<char>
{
    private readonly char[] _buffer = new char[80];

    public LineBuffer(ReadOnlySpan<char> buffer)
    {
        int number = (_buffer.Length < buffer.Length) ? _buffer.Length : buffer.Length;
        for (int i = 0; i < number; i++)
            _buffer[i] = buffer[i];
    }

    public IEnumerator<char> GetEnumerator() => _buffer.AsEnumerable<char>().GetEnumerator();
    IEnumerator IEnumerable.GetEnumerator() => _buffer.GetEnumerator();

    internal static LineBuffer Create(ReadOnlySpan<char> values) => new LineBuffer(values);
}
```

The official documentation says the builder must be named "Create," but that's
false. We can name it however we want as long as it matches the attribute (it's
probably still worth adhering to the suggested practice.)

- Adding collection expression support to custom types is helpful in your
codebase, even more so if you're a library author.

- The syntax of collection expressions is symmetric with that of slicing and
pattern matching, a nice touch that keeps the language tidy and coherent. Take a
look at this pattern matching switch:

```cs
public Grade GPA => Grades switch
{
    [] => 4.0m,
    [var grade] => grade,
    [.. var all] => all.Average()
};
```

- Visual Studio, VS Code, JetBrains Rider and most other IDEs offer full support
for refactoring old-style collection initializations to collection expressions.

- What about dictionary expressions? They are common in other languages (again,
Python). When asked, Kathrine Dollard of the C# design team answered that
they're thinking about it, mostly trying to understand the best design, so
there's a chance that we'll see dictionary expressions in the language in the
future.

Also see: [C# 12 Primary Constructors](/csharp-primary-constructors/).
