---
date: 2025-08-28T10:07:05+02:00
title: "Invoicetronic, or what I've been working on recently"
tags: ["invoicetornic", "golang", "mcp", "ai", "invoicing"]
---

The most recent project I worked on is [Invoicetronic](https://invoicetronic.com/en/), a modern API for complete management of the electronic invoicing cycle in Italy (FatturaPA/SDI).

We had long used an internal API by our accounting software, which was also utilized by thousands of our end users. We decided to make our experience and expertise available to external developers, allowing them to integrate electronic invoicing into their applications quickly via a public API. Thus, the Invoicetronic project was born.

We had made a similar choice in the past with the open-source release of [FatturaElettronica.NET](https://github.com/FatturaElettronica/FatturaElettronica.NET), also a library initially created for internal use. [Eve](https://python-eve.org) and [Cerberus](https://python-cerberus.org) for Python started as an internal projects too.

We didn't limit ourselves to just opening our API to the public. That alone would have been challenging (as any veteran well knows, opening a private product to a broader and more diverse audience is already a real challenge in itself). We seized the opportunity, years after its creation and with millions of invoices having passed through the system in the meantime, to refresh the design, improve performance, and add [important features](https://invoicetronic.com/en/features/) that proved stimulating to implement.

I certainly wasn't lacking experience with REST APIs, but I still learned a lot, especially while working on the tools accessory to the actual API. An example is the client [SDKs](https://invoicetronic.com/en/docs/sdk/). We support all the most common programming languages: JavaScript/TypeScript, Python, PHP, Java, C#, Ruby, and Go. They're built using OpenAPI Generator, a tool I initially underestimated but which turned out to be excellent, thanks also to the remarkable ecosystem built by the community. Working on the SDKs also provided me with the opportunity to improve my Continuous Integration skills. Beyond the usual test-containerization-staging-deploy cycle, every API update is followed by an automatic release of all SDKs, each with deployment on both GitHub and the reference package manager for the language: PyPI, NuGet, npm, etc. Seemingly obvious tasks (such as inferring the new API version number from CI and then reusing it in the package version of individual SDKs) required considerable brainstorming.

The Invoicetronic project, which gave me the most satisfaction and taught me the most, is [`invoice-cli`](https://invoicetronic.com/en/docs/cli/#invoice). This [open source](https://github.com/invoicetronic/invoice-cli) command-line tool enables sending and receiving electronic invoices from the terminal, and is available for Linux, Mac, and Windows. You don't need to be a developer or study the API in depth to use it, and, not secondarily, it can be conveniently inserted into a script. A trivial usage example would be:

```
# send a single invoice.
$ invoice send file1.xml

# send multiple invoices, then delete the local copies.
$ invoice send *.xml --delete

# individually send multiple files.
$ invoice send file1.xml file2.xml file3.xml

# receive all unread invoices.
$ invoice receive --unread
```

From my point of view, though, the interesting thing about `invoice` is that it's written in Go, a language I hadn't yet had the chance to use professionally. A veteran would likely find fault with the implementation details and the chosen approach, but I hope they'll be merciful, considering I'm a beginner in this space. We could have used C#, which is now our reference language. Still, in the case of the command-line, Go seemed like a better choice, first of all, for the exceptional support in creating native multi-platform binaries, then for performance both cold and hot, and for deployment simplicity. If I had to make another command-line tool, I would return to Go rather than orient myself toward languages I know better and with which I'm more comfortable, like Python and C# (speaking of C#, the recent improvements in AOT and cross-platform support are remarkable - we're on the right track, come on guys!)

A second stimulating project was the [Invoicetronic MCP Server.](https://invoicetronic.com/en/features/#llm-and-ai-integration) We were interested in having developers interact with the Invoicetronic API via LLM, and an MCP server serves precisely that purpose. Fortunately, C# has an excellent official library (still in preview but sufficiently mature) that simplifies the work, and implementing and deploying a first experimental version was relatively simple. There is enormous potential in this area, and I want to stay on top of it: objective achieved (I also gave a [couple](https://nicolaiarocci.com/im-speaking-at-devmarche-summer-ai-afternoon/) of [presentations](https://nicolaiarocci.com/mcp-or-connecting-our-apps-to-llms/) on the topic).

We released Invoicetronic for our own use, but I hope other developers will adopt it. Throughout many years of activity, our primary client has consistently been the end-user, the company that utilizes our accounting applications. In recent years, we also engaged with developers, but only in the context of our open-source projects. I'd love to serve them professionally as well.