---
date: 2024-02-20T11:48:42+01:00
title: Default ASP NET Core 8 port changed from 80 to 8080
tags: ["til", "dotnet", "docker"]
---
Today, I learned the hard way that the default port for ASP.NET Core 8 container
images has been updated from port 80 to 8080, quite a remarkable breaking
change.

We upgraded our web application from .NET 7 and let the CI pipeline do its work.
Finally, we checked the application in the browser to ensure everything was
okay, but unfortunately, we got a 502 Bad Gateway error. The Nginx logs revealed
that the app was rejecting connections, which was unexpected because we didn't
make any changes there. Further investigation showed that the web app listened
on port 8080 while Nginx was reverse-proxied to 80. So that was the problem. But
why did the port change?

> The change to the port number was made because of the need to provide a good
usability experience when switching to a non-root user. Running as a non-root
user requires the use of a non-privileged port in some environments. Since port
80, the previous default port, is a privileged port, the default was updated to
port 8080, which is a non-privileged port *([source](https://learn.microsoft.com/en-us/dotnet/core/compatibility/containers/8.0/aspnet-port#reason-for-change))*

It all makes sense now. In hindsight, it was our mistake. We should have
explicitly declared the port in our launch settings anyway. As the [Python
Zen](https://en.wikipedia.org/wiki/Zen_of_Python) says, "Explicit is better than
implicit."