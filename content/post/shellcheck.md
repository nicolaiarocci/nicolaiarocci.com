---
date: 2024-07-24T14:59:21+02:00
title: ShellCheck
tags: ["til", "bash", "linux"]
---
Today I [learned](https://www.simplermachines.com/how-to-write-better-bash-than-chatgpt/) about [ShellCheck](https://github.com/koalaman/shellcheck), a static analysis tool that "finds bugs in your scripts". It can and should be run on the command line, but an [online version](https://www.shellcheck.net) is also available. It catches most style and syntax errors and has plenty of options, like ignoring specific errors and warnings, which is helpful in CI scenarios. 