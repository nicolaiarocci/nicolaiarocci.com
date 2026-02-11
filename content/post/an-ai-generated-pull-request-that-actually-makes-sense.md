---
date: 2026-02-11T09:57:15+01:00
title: An AI-generated pull request that actually makes sense
tags: ["ai", "open source", "eve"]
---

Yesterday a [pull request](https://github.com/pyeve/eve/pull/1567) came in proposing a fix for a small pagination bug in [Eve](https://python-eve.org), the REST API framework I maintain. The intervention is small, precise, and comes with a well-crafted test.

Two things stood out: the PR is in draft, and it includes an AI disclosure:

> the fix and the test were created by Claude. I don't have mongo available or all the necessary python versions for testing, so I'm making this a draft PR so that I can verify all the tests/checks pass before marking it as ready to review.

I'm not at all surprised that Claude was used for the fix (I use it daily myself, to great benefit), but I appreciate the disclosure. A careful review of the code wouldn't have revealed AI involvement.

The idea of submitting a draft to let the CI run and intervene where needed before marking it as ready for review is also smart — especially since, as the author explains, they can't run the tests locally.

All in all, an exemplary case of AI use in open source, and welcome news at a time when maintainers are under pressure, often flooded with auto-generated junk PRs (in my own small corner, it [has happened](https://github.com/pyeve/eve/pull/1548) to me too). As always, it's not the tool that's the problem — it's who uses it, and _how_.