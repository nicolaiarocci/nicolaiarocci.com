---
date: 2022-09-07T07:05:25+01:00
title: "Eve 2.0.1 released"
share: false
tags: ["eve", "open-source", "python"]
---
Today I released [Eve 2.0.1][1], which contains an essential fix if you're
using `MONGO_URI` to connect to your MongoDB instance. See the [relevant
ticket][2] for details. I've also pinned Flask dependency to v2.1, as v2.2
brings some breaking changes that, you guessed it, break our CI runs. If you
think you can help wiht that, [please do so][3]. The complete changelog is
available [here][4].

![](/images/eve-2.0.1.png)

