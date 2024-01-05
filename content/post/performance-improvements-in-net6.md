---
date: 2021-09-03T07:05:25+01:00
title: "Performance improvements in .NET6"
share: false
tags: ["links", "dotnet", "programming"]
---
I'm pretty psyched about the upcoming .NET6 release. I've already [touched][1]
on ASP.NET 6 Minimal APIs. Continuing on the long-established tradition, the
team has also worked hard on the performance side of things. File IO, for
example, is seeing [impressive gains][2]:

> For .NET 6, we have made FileStream much faster and more reliable, thanks to
> an almost entire re-write. For same cases, the async implementation is now
> a few times faster! We also recognized the need of having more
> high-performance file IO features: concurrent reads and writes,
> scatter/gather IO and introduced new APIs for them. TL;DR File I/O is better,
> stronger, faster!

If you have the time, make sure you read the whole blog post. Learning about
the low-level details on how they achieved such (pretty phenomenal) results is
fascinating. They're not stopping at file IO either. In another [lengthy blog
post][3], they had to add a table of contents, or we would get lost in the myriad
of improvements.

> Don’t worry, I don’t cover all of them here, but grab a large mug of your
> favorite hot beverage, and settle in: this post takes a rip-roarin’ tour
> through ~400 PRs that, all together, significantly improve .NET performance
> for .NET 6.

There are [a][4] [ton][5] [of][6] [new][7] [things][8] [coming][9] [up][10],
too, of course.

