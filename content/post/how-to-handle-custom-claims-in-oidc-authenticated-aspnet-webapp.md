---
date: 2024-05-31T15:53:30+02:00
title: How to handle custom claims in an Open ID Connect-authenticated ASP.NET Core app
slug: how-to-handle-custom-claims-in-an-oidc-authenticated-aspnet-core-app
tags: ["csharp", "dotnet", "til"]
---
Today, I learned how to handle custom claims in an Open ID Connect authenticated ASP.NET Core app.

The scenario goes like this. I have an ASP.NET Core app that authenticates with Open Id Connect. It receives a bearer token from the authentication server. Besides OIDC claims, this token has been forged with additional custom claims for use in the app. However, only ODIC claims exist when I parse `HttpContext.User.Identity.Claims` in my middleware. If I retrieve the token with `HttpContext.GetTokenAsync` and decode it, I confirm it contains all the claims I need. Where have my custom claims gone? Or, how can I get `User.Identity` to provide them along with the OIDC ones?

As it turns out, one must hack them into the `User.Identity.Claims` collection by hand. That's done by leveraging the `OnTokenValidated` event handler like this: 

```cs
authenticationBuilder.AddOpenIdConnect("oidc", options =>
{
    options.Authority = "authority";
    options.ClientId = "client_id";
    options.ClientSecret = "secret";
    options.ResponseType = "code";

    ...
    options.GetClaimsFromUserInfoEndpoint = true;
    options.SaveTokens = true;
    options.Events = new()
    {
        OnTokenValidated = context =>
        {
            // adds custom claims from the token into Principal.Identity
            if (context.Principal?.Identity is not ClaimsIdentity claimsIdentity) return Task.CompletedTask;
            
            var accessToken = context.TokenEndpointResponse?.AccessToken;
            if (string.IsNullOrEmpty(accessToken)) return Task.CompletedTask;
            
            var handler = new JwtSecurityTokenHandler();
            if (handler.ReadToken(accessToken) is not JwtSecurityToken jsonToken) return Task.CompletedTask;
            
            foreach (var claim in jsonToken.Claims)
                if (claimsIdentity.Claims.All(c => c.Type != claim.Type))
                    claimsIdentity.AddClaim(claim);

            return Task.CompletedTask;
        }
    };
});
```

Is there a better and less hacky way to achieve the same result? Please let me know.
