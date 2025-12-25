---
date: 2025-06-10T18:11:36+02:00
title: People won't use IDEs anymore
tags: ["links", "ai", "claude"]
---
I'm just back from watching [Mastering Claude Code in 30 Minutes](https://www.youtube.com/live/6eBSHbLKuN0), a talk by Boris Cherny, who, I learned, created Claude Code. I was struck by Boris's reply to one question from the crowd: 

_Hey, why did you build a CLI tool instead of an IDE?_

> Yeah, it's a good question. There are two reasons. We started this at Anthropic, where people use a broad range of IDEs. Some people use VS code. Other people use Zed, Xcode, Vim, or Emacs. And it was just hard to build something that works for everyone. And so the terminal is just the common denominator. The second thing is that at Anthropic, we see firsthand how quickly the model is improving. **I think there's a good chance that by the end of the year, people won't use IDEs**. And so, we want to prepare for this future and avoid over-investing in UI and other layers on top. Given the way the models are progressing, it may not be practical to work on them soon.

Well, that's one fascinating bold statement right there. It aligns with a vision I've had for a while: in a not-too-distant future, people will use LLM UIs (think Claude.ai with plug-and-play MCP support and voice recognition[^1] both built in) as their primary interface instead of many different, specialized applications, at least for most use cases.

[^1]: One remarkable suggestion from the talk is to use macOS voice dictation instead of typing prompts to Claude Code.