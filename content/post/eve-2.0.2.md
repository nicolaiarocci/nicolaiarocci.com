---
date: 2022-09-23T07:05:25+01:00
title: "Eve 2.0.2 released"
share: false
tags: ["python", "open-source", "eve"]
---
Eve 2.0.2 was [just released today][1]. It fixes a problem introduced with v2.0
in which ETag generation failed if `uuidRepresentation` was not set in
`MONGO_OPTIONS`. See [issue #1486][2] for details. Many thanks
[@tgm](https://github.com/tgm-git) for reporting and then contributing the fix.

