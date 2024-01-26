---
date: 2024-01-26T09:31:47+01:00
title: "Fixing the \"Failed to create CoreCLR error 0x80070008\" error when starting a .NET 8 docker container"
slug: fixing-the-failed-to-create-coreclr-error-0x80070008-error-when-starting-a-dotnet-docker-container
tags: ["til", "dotnet", "docker"]
---
Another day, another unexpected problem. Launching a .NET 8 app from a docker
container, I got this error: `Failed to create CoreCLR, HRESULT: 0x80070008`.

I was puzzled as the same container ran smoothly in our test environment but not
in production. I ruled out resource problems (memory or disk full, maybe?) but
then compared the Docker Engine versions we run in test and production. Both
were old (20. xx when 25 is available), but interestingly, the production
version was older. I searched online and found a two years-old
[ticket](https://github.com/PowerShell/PowerShell/issues/17624) hinting at some
problems between .NET 8 and older Docker versions.

I
[updated](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
the Docker Engine to the latest version, and guess what? The .NET 8 container
now starts without making a dent.