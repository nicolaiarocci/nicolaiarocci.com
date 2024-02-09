---
date: 2024-02-09T15:58:54+01:00
title: GitHub Wikis don't allow edits or pull requests
tags: ["til", "github", "wikis"]
---
Today I learned that GitHub wikis are not editable online and [do not support
pull requests](https://github.com/orgs/community/discussions/50163). You can
clone and edit a wiki locally but not return your change to the original
repository. 

I don't use wikis in [my projects](/opensource/); I prefer documentation to stay with the
project, usually in a dedicated directory, and publish it on a dedicated site
through GitHub Pages. But today was different as I [opened a pull
request](https://github.com/adityatelange/hugo-PaperMod/pull/1419) for PaperMod,
the Hugo theme I use on this website. Someone asked if I could update the
documentation too. Right, too bad it's impossible to do that.

The first ticket on this [goes back to
2016](https://github.com/isaacs/github/issues/846). This limitation makes GitHub
wikis impractical for any team project (maybe 90% of those on the platform),
confining them to personal projects or small experiments. No wonder so many
Wikis appear as outdated on GitHub. 

It would be better to withdraw the feature given that GitHub offers a much more
compelling solution in Pages.