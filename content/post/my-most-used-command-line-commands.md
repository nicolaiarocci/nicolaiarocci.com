---
date: 2025-01-01T12:33:34+01:00
title: My most used command-line commands
tags: ["bash"]
---
My most used command-line commands:

1. 5180 `git`
2. 777 `cd`
3. 653 `ls`
4. 452 `go`
5. 440 `./invoice`
6. 377 `dotnet`
7. 373 `rm`
8. 270 `vi`
9. 225 `cat`
10. 219 `ssh`

Version control dominates the scene (a gentle middle finger for the youngster - you know who you are - who told me I should not be coding anymore). I also like that the list hints at the new stuff I've been working on recently and am excited about.

Generated with `history | awk '{print $2}' | sort | uniq --count | sort --numeric-sort --reverse | head -10` and inspired by [Chris De Luca](https://www.chrisdeluca.me/2024/12/31/my-cli-wrapped-most-used.html).