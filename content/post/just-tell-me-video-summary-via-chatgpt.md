---
date: 2024-02-06T09:45:04+01:00
title: YouTube video summaries via ChatGPT
tags: ["links", "llm", "ai", "youtube"]
---
[Just Tell Me](https://just-tell-me.deno.dev) cleverly leverages ChatGPT to
provide short, insightful summaries of YouTube videos. 

> Have you ever wasted some time watching a youtube video, that got you kind of
interested because of the click-baity topic, but in the end turned out to be
nothing more BUT click-bait? Or have you ever wanted to just quickly recall what
a video that you've watched some time ago was about? Just Tell Me has you
covered!

You can run it from the website or
[locally](https://github.com/franekmagiera/just-tell-me) on the command line,
with your OpenAPI key and the LLM model of choice. I have not looked at the
code, but I understand it leverages the video transcript to do its magic[^1]. I've
been using it for a while, and it's been good.

[^1]: I've now looked at the code and the actual ChatGPT prompt is *"You will be provided with video captions. Summarize the video in one paragraph"*
([link](https://github.com/franekmagiera/just-tell-me/blob/04be5af4de743ca99d4480a9576830416ec3415e/app/src/get-captions-summary.ts#L23)).