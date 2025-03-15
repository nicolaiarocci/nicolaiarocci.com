---
date: 2025-03-15T07:47:30+01:00
title: A 10x faster TypeScript, but that's not the point
tags: ["typescript", "hejlsberg", "microsoft", "programming"]
---
[Anders Hejlsberg][1] is a legend in my field, with Turbo Pascal, Delphi, C#, and TypeScript in his palmares. This week, he [announced][2] a rewrite of the TypeScript compiler, leading to a stunning 10x performance boost. This remarkable achievement is due to two main factors: the adoption of Go for the compiler and the Language Server Protocol and the high parallelism that Go enables. Previously, the compiler itself was in TypeScript, which severely hindered performance. 

Two things strike me about this story.

The [video][3] is worth watching. Not so much for the content itself but for the delivery. No emphasis, special effects, marketing crap, visual tricks, or star tricks whatsoever. The strength is in the message; any addition would be a distraction. I was fortunate enough to attend a few meetings with Hejlsberg at the Microsoft Campus in Redwood, and, well, emphasis and hyperbole are certainly not his style. He's genuinely a down-to-heart type of guy. On the other hand, he is Danish, not American.

For purely business reasons, Microsoft could have forced the choice of one of its languages for the rewrite. Of course, none of those would have been ideal, least of all C# (itself a Hejlsberg creature), but corporate reasons could easily have prevailed. Hejlsberg and his team could pick the best tool for the job. Go is the lowest-level language with a GC; it compiles natively on all platforms, has great parallelism support, and you can write excellent functional code with it. It says a lot about Microsoft, the cultural shift it has managed since the late 1990s and early 2000s, and how it stays relevant today, unlike many of its competitors of those times.

I am concerned that by switching to Go, they will no longer dogfood the language. By their admission, maintaining that massive compiler codebase in TypeScript was instrumental in adequately developing the language. We'll see how that pans out now that they're not working TypeScript daily.

I'll end by quoting a YouTube commenter who nailed it in one sentence: 

> Imagine creating several languages but still choosing a different one for your compiler rewrite because it's just the best tool for the job - absolute ego-less GOAT move.

[1]: https://en.wikipedia.org/wiki/Anders_Hejlsberg
[2]: https://devblogs.microsoft.com/typescript/typescript-native-port/
[3]: https://youtu.be/pNlq-EVld70?si=BOlGs8g1pwBpCEqz