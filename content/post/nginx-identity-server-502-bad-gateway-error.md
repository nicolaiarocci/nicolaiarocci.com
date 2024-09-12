---
date: 2024-09-12T16:17:58+02:00
title: "Under ASP.NET 8, NGINX returns 502 Bad Gateway after authentication by IdentityServer"
slug: under-aspnet-8-nginx-returns-502-bad-gateway-after-authentication-by-identityserver
summary: "Today, I learned the hard way that NGINX has default buffer sizes, which can cause trouble in specific scenarios like mine."

tags: ["til", "dotnet", "nginx", "identityserver"]
---

Today, I learned the hard way that NGINX has small buffer sizes, which can cause trouble in specific scenarios like mine.

We have two ASP.NET 8 applications behind NGINX; one is a regular web app, and the other is an auth server built with Duende Identity Server. When the user attempts to log in to the web app, they are sent to the auth server; once logged in, they are sent back to the app, and that's when NGINX returns a weird 502 Bad Gateway. Upon inspecting the NGINX logs, I found the following error:

    upstream sent too big header while reading response header from upstream

Some digging revealed that NGINX has a pretty small default buffer size, and proxying auth requests (with their typically above-average-size headers) back and forth is prone to breaking that limit.

The fix is straightforward: raise those buffer sizes. Most blogs suggest doing that globally, but that seems overkill, as NGINX buffering can be configured per server and location blocks. You may want to keep the global defaults and only raise them (along with memory consumption) for locations that need it.

```
  location {
    ...
    proxy_buffers 4 256k;
    proxy_buffer_size 128k;
    proxy_busy_buffers_size 256k;
    ...
  }
```

Mind you, the above values (that I found in almost every blog dealing with this problem) are likely too big and should be trimmed down. That's my next task, using [this](https://www.getpagespeed.com/server-setup/nginx/tuning-proxy_buffer_size-in-nginx) excellent article for guidance.