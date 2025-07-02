---
date: 2025-07-02T09:57:57+02:00
title: "Cloudflare to introduce pay-per-crawl for AI bots"
tags: ["links", "llm", "ai", "cloudflare"]
---
The biggest news in tech this week (which isn't over yet) is, without a doubt, that [Cloudflare is about to introduce a pay-per-crawl model for AI bots](https://blog.cloudflare.com/introducing-pay-per-crawl/)—huge in many ways, as let's not forget that approximately 20% of internet traffic is routed through Cloudflare.

I have many thoughts right now, and it will take some time for them to settle. A good analysis and explanation of why this move is needed and is a good first step can be found in yesterday's article by Dries Buytaert's, [The Web's Broken Deal with AI Companies](https://dri.es/the-webs-broken-deal-with-ai-companies), which I recommend everyone read.

> For 25 years, we built the Open Web on an implicit agreement: search engines could index our content because they sent users back to our websites. That model helped sustain blogs, news sites, and even open source projects. AI companies broke that model. They train on our work and answer questions directly in their own interfaces, cutting creators out entirely. Anthropic's crawler reportedly makes 70,000 website requests for every single visitor it sends back. That is extraction, not exchange.

The ongoing discussion on [Hacker News](https://news.ycombinator.com/item?id=44432385) is also worth reading

Side note, I am fascinated by the [technical details](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/402) surrounding the 402 Payment Required response (and [Cloudflare's implementation](https://blog.cloudflare.com/introducing-pay-per-crawl/#publisher-controls-and-pricing)), which was designed explicitly for micro-payment handling but never gained traction, until now.