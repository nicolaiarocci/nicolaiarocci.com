---
date: 2024-07-22T15:51:51+02:00
title: "Bash-Oneliner: a collection of terminal tricks for Linux"
tags: ["links", "til", "bash"]
---
[Bash-Oneliner](https://github.com/onceupon/Bash-Oneliner) is an excellent resource for Bash/Linux users. Most of the "tricks" are well-known, but there is always something to learn. More importantly, finding them all well organized in one file is rare.

I use the reverse lookup of bash-history (Ctrl+R) daily. Still, only today (thanks to an HN [comment](https://news.ycombinator.com/item?id=41033120) on Bash-Onliner) did I learn that it also preserves one's comments, which can be exploited to invoke complex commands quickly:

```bash
$ mv -n ~/Desktop/*.pdf ~/Documents/PDF_Archive/  #pdfsync
```

Then, you simply Ctrl-R and type "pdfsync" to recall the above command when needed. Neat.