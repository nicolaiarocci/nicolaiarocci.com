---
date: 2024-01-17T18:28:14+01:00
title: How to implement a PKCE code challenge in C#
slug: how-to-implement-pkce-code-challenge-in-csharp
tags: ["til", "pkce", "dotnet", "csharp", "programming"]
---
Today's fun was implementing OAuth2's [RFC
7636](http://tools.ietf.org/html/rfc7636)'s PKCE (Proof Key for Code Exchange)
in C#. It's relatively straightforward, but I decided to share my implementation
should it be helpful to someone else out there. 

> PKCE  is an extension to the Authorization Code flow to prevent CSRF and
authorization code injection attacks. [..] It was originally designed to protect
the authorization code flow in mobile apps, but its ability to prevent
authorization code injection makes it useful for every type of OAuth client,
even web apps that use client authentication
([source](https://oauth.net/2/pkce/)).

In a nutshell:

1. The client requests a single-use authorization code to an authentication server. In doing that, it includes a `code_challenge` with the request. 
2. The server responds with the authorization code if the client is recognized and authorized. 
3. The client requests an access token in exchange for the authorization code. It includes the `code_verifier` used to generate the original `code_challenge`; 
4. The server confirms that the verifier is the same one used to generate the code challenge; hence, the client is the same.

Plenty of excellent documentation is online (like
[here](https://auth0.com/docs/get-started/authentication-and-authorization-flow/authorization-code-flow-with-proof-key-for-code-exchange-pkce).)

I was interested in `code_verifier` and `code_challenge` generation. Here's my implementation:

```cs
/// <summary>
/// Provides a randomly generating PKCE code verifier and it's corresponding code challenge.
/// </summary>
public static class Pkce
{
    /// <summary>
    /// Generates a code_verifier and the corresponding code_challenge, as specified in the rfc-7636.
    /// </summary>
    /// <remarks>See https://datatracker.ietf.org/doc/html/rfc7636#section-4.1 and https://datatracker.ietf.org/doc/html/rfc7636#section-4.2</remarks>
    public static (string code_challenge, string verifier) Generate(int size = 32)
    {
        using var rng = RandomNumberGenerator.Create();
        var randomBytes = new byte[size];
        rng.GetBytes(randomBytes);
        var verifier = Base64UrlEncode(randomBytes);

        var buffer = Encoding.UTF8.GetBytes(verifier);
        var hash = SHA256.Create().ComputeHash(buffer);
        var challenge = Base64UrlEncode(hash);

        return (challenge, verifier);
    }

    private static string Base64UrlEncode(byte[] data) =>
        Convert.ToBase64String(data)
            .Replace("+", "-")
            .Replace("/", "_")
            .TrimEnd('=');
}
```

Usage is as simple as:

```cs
var (challenge, verifier) = Pkce.Generate();
```

In ASP.NET Core you don't usually need to mess with PKCE as the framework
supports it very transparently, but the project I'm working on right now is bare
and to the bones, with no ASP.NET Core in sight, so I had to bring my own
implementation. Fun stuff.