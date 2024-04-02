---
date: 2024-04-02T15:30:03+02:00
title: Timeline of the XZ open source attack
tags: ["open source", "security", "links"]
---
The so-called "XZ attack" is all over the internet these days, and for good
reason.

> Over a period of over two years, an attacker using the name “Jia Tan” worked
as a diligent, effective contributor to the xz compression library, eventually
being granted commit access and maintainership. Using that access, they
installed a very subtle, carefully hidden backdoor into liblzma, a part of xz
that also happens to be a dependency of OpenSSH sshd on Debian, Ubuntu, Fedora,
and other systemd-based Linux systems. That backdoor watches for the attacker
sending hidden commands at the start of an SSH session, giving the attacker the
ability to run an arbitrary command on the target system without logging in:
unauthenticated, targeted remote code execution.

As the excellent [timeline of the xz open-source
attack](https://research.swtch.com/xz-timeline) quoted above remarks,
this will likely be remembered as the first known supply chain attack on widely
used open-source software. This story screams a nation-state-level hacking
attempt to me.

As an open-source maintainer with limited bandwidth, I know very well how
tempting it can be to give up control and how difficult it is to judge someone's
intentions. I feel for the original author of XZ. A relevant discussion is
currently going on on [HN](https://news.ycombinator.com/item?id=39902241).