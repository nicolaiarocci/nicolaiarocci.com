---
date: 2025-06-18T10:36:39+02:00
title: MCP Remote
tags: ["til", "mcp", "llm"]
---
I've been implementing a remote [MCP Server](https://modelcontextprotocol.io). It comes with a hybrid authentication system that supports the OAuth2 flow and, as a backup, a custom header for those simple clients that cannot handle OAuth. One such client is Claude Desktop, which, at this time, is even worse; it only supports STDIO (local) servers, let alone OAuth2.

Today I learned about a nice NPM package called [MCP Remote](https://www.npmjs.com/package/mcp-remote), which bridges the gap by allowing MCP clients that only support local servers to connect to remote MCP Servers, even with authentication support. Thanks to this tool, Claude Desktop is now talking to my remote server[^1]. 

The only problem is that the OAuth2 handshake is not initiated at Claude startup or the first 401 response, as I expected, so I had to fall back to my secondary authentication method, the custom header. 

I could, of course, retrieve my OAuth2 token out of band and then pass it to MCP Remote, but that's cumbersome and boring. For now, I'm satisfied with the custom header approach. It's only a matter of time before Claude Desktop matures enough to fully support Remote MCP servers. Right?

[^1]: For testing purposes, I primarily resort to [MCP Inspector](https://modelcontextprotocol.io/docs/tools/inspector), the reference tool; however, it's also nice to experiment with a reference large language model (LLM), mainly to assess the potential once the server is connected to it.
