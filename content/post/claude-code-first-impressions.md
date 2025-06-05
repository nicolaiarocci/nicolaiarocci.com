---
date: 2025-06-05T18:02:55+02:00
title: Claude Code first impressions
tags: ["llm", "claude", "ai"]
---
Since yesterday, Claude Code has been included in the Pro subscription we're signed up for. I'd been wanting to try it for a while, and now nothing was stopping me. Only yesterday (a curious coincidence), I read [AI Changes Everything](/ai-changes-everything/) by Armin Ronacher, which gave me a glimpse of the potential and made my hands itch to try it.

The initialization of Claude on the repository surprised me; the analysis (reported in CLAUDE.md) is thorough and reveals a good understanding of the project, including both the code and the general functioning, strategies, techniques, technologies and libraries employed. 

I asked Claude to generate a test suite from scratch, and it did so rather effortlessly (it went back and forth a few times, and it is fascinating following its reasoning and attempts from a distance). Claude added the tests to the existing project, a big no-no for me. I asked it to go back and create a dedicated test project, and it complied, adding the new project to the solution. It took several iterations to achieve a good result. We now have 134 tests that cover 98% of the project's business logic. Upon request, Claude also added code coverage by installing the missing tools.

Once satisfied with the test suite and having committed and pushed (via Claude) the work done, I asked Claude to set up a GitHub Action to run the tests on every push, then to update the existing workflows (container build; deployment to test or production; etc.) so they all run tests first.

In half a day of work, during which I mostly did other things, such as helping a colleague while Claude was chugging away, I achieved what would have taken me a week or even just a few days.

I have very little to complain about in terms of code quality, and where I wasn't satisfied, I informed Claude and the unsatisfying code was quickly and pleasantly refactored. However, some refactoring is better done with Rider because it's faster, doesn't miss anything (like Claude tends to do if there are multiple similar refactorings to be done and they are scattered across various files) and doesn't waste tokens that count toward usage limits (with the Pro subscription, we have access to a lighter tier of Claude Code. You want the Max subscription for unlimited - or higher anyway- ceiling).

One valuable feature is memory. You can have Claude memorize directives. This memory can be local to the repo or global. I instructed Claude to prefer collection expressions and utilize C#'s new targeted-type initialization feature, among other things, which were duly noted. I then asked Claude to refactor in light of the new directives, and it did. New code is now produced according to my preferences, and it will be on all my projects.

A thorough code review is always necessary, of course, but wouldn't you do that for any code coming into your project? 

Color me impressed so far. Copying and pasting from LLM's web UIs is already a thing of the past. The present is all about agents, and they're just getting started.