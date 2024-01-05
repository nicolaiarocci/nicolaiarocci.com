---
date: 2022-03-01T07:05:25+01:00
title: "You're probably using the wrong dictionary"
share: false
tags: ["links", "dictionary"]
---
In 2014, James Somers sat down to write a beautiful, entertaining lament about
the state of today’s dictionaries and an argument in favor of the adoption of
Noah Webster’s 1913 edition.

> I don't want you to conclude that it's just a matter of aesthetics. Yes,
> Webster's definitions are prettier. But they are also better. They're so much
> better that to use another dictionary is to keep yourself forever at arm's
> length from the actual language.

> Recall that the New Oxford, for the word "fustian," gives "pompous or
> pretentious speech or writing." I said earlier that that wasn't even really
> correct. Here, then, is Webster's definition: "An inflated style of writing;
> a kind of writing in which high-sounding words are used, above the dignity of
> the thoughts or subject; bombast." Do you see the difference? What makes
> fustian fustian is not just that the language is pompous—it's that this
> pomposity is above the dignity of the thoughts or subject. It's using fancy
> language where fancy language isn't called for. It's a subtle difference, but
> that's the whole point: English is an awfully subtle instrument. A dictionary
> that ignores these little shades is dangerous; in fact in those cases it's
> worse than useless. It's misleading, deflating. It divests those words of their
> worth and purpose.

You can read it all [here](http://jsomers.net/blog/dictionary). It's worth your
time..

Not happy with the essay alone, he also added instructions on installing
Webster's on a Mac. Unfortunately, I could not get them to work on Catalina:
the DictUnifier app would crash as soon as I dragged the [dictionary file][4]
on it. A little research revealed that DictUnifier has a [problem with
Catalina][2]. The suggested workarounds did not work for me. In the process,
I learned that DictUnifier has gone unmaintained. Thankfully, a couple of years
ago a good soul released [DictConv][3], a "Node.js version of DictUnifier".
DictConv did the trick. Webster's 1913 is now happily residing in my macOS
Dictionary.

![Webster's 1913](/images/webster1913.png)
