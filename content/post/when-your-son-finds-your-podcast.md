---
date: 2025-12-22T10:49:22+01:00
title: "Rediscovering a 2021 podcast on Python, .NET, and open source"
tags: ["podcast", "python", "csharp"]
---

Yesterday, the kids came home for the Christmas holidays. Marco surprised me by telling me that on his flight from Brussels, he discovered and listened to “my podcast” on Spotify. I was stunned. I didn't remember ever recording a podcast, even though I've given a few interviews here and there over the years. 

During my usual morning walk today, I went to look for it, and [there it was](https://open.spotify.com/episode/1xPawIlPhVKnnXcP4PxtC6?si=b1931340af1048de), an interview I had done in 2021 that I had completely forgotten about. I got over the initial embarrassment (it's always strange to hear your own voice) and resisted the temptation to turn it off, listening to it all the way through. I must admit that it captures that moment in my professional life, and much of the content is still relevant, especially regarding my experience as an open-source author and maintainer and my transition from C# to Python and back.

I found copies of the podcast on many platforms, including a [YouTube video](https://youtu.be/D8chi-YA5Uc?si=tkDKK2gWdAG1vsfU) (we actually video recorded it, who knew!), but they are all in Italian. I fed the video to MacWhisper, which transcribed it; I then asked Claude to translate it into English, removing pauses and repetitions; and finally, I ran it through Grammarly for a grammatical check. That’s what AI allows today: half an hour to go from an Italian audio podcast to a full English transcript, and that’s including a manual, pedantic review of Grammarly suggestions.

What follows is the full transcript, in English, of that 2021 interview. We touch on a variety of topics, including Python for .NET Developers, functional programming in Python, F#, and C#, the Eve REST framework and Flask, electronic invoicing, my open-source experience as an author and maintainer in both ecosystems, cross-platform development, and advice to newcomers. 

I don’t really know how or why Marco found this relic of mine on Spotify, and I'm not brave enough to ask, but I’m grateful he dug it up. Also, many thanks to Mauro Servienti for hosting the interview.

## DotNet Podcast - Interview with Nicola Iarocci (2021)

_Hello everyone, and welcome to a new episode of DotNet Podcast, the Italian podcast dedicated to Microsoft technologies and more. You can find us on all major social platforms and podcasting services; all links are on our website, dotnetpodcast.com. Today we're talking about Python and Eve (or Pyrrest) and, why not, electronic invoicing for .NET._

_Today I have the pleasure of having Nicola Iaroci with me. I met Nicola at the Italian edition of SoCraTes in Rimini a few years ago. Nicola is the classic jack of all trades: developer, entrepreneur, fitness enthusiast, consultant, open-source lover, Microsoft MVP, MongoDB Master, and probably something else I've forgotten, because the list is very long. In the open source world, he's known primarily for Eve (we'll have him explain how to pronounce it), a REST framework for Python, and Electronic Invoicing .NET. I almost forgot: if you want to know anything about how Git works, Nicola knows it all._

__Welcome Nicola! Did I forget anything?__

Hi, thanks, welcome everyone. Well, no, I'd say probably yes, but I can't tell you what, so I'd say the introduction is perfect. Thanks.

__This podcast has always been oriented toward the .NET world, though lately we're branching out a bit into various technologies and even topics not necessarily technical. But assuming our listeners are primarily .NET developers, briefly, what is Python, and why should or could a C# .NET developer be interested?__

Sure, so first of all, Python fundamentally, let's say from a general point of view, is not that different from the languages we're used to in the .NET world, particularly C#, in the sense that it's still a high-level language, object-oriented from its foundations, let's say, from its roots. The main difference, perhaps, is that it's fundamentally interpreted, so there's an interpreter that executes the language and programs, although it's also possible to do JIT compilation, especially for performance reasons.

I'll add an important note because people generally think that a dynamic language is not strongly typed, which is not true. Python is a strongly typed language, but it has dynamic semantics, so type checking is still possible. I always clarify this because those coming from C-derived languages often think it's very similar to JavaScript, when in reality, there are clear differences.

It's certainly a language designed to be more approachable for a general programmer or even a beginner, and this probably also explains why it's had such success, I'd say almost incredible success, for example, in the world of scientific research, numerical computing, in the financial world and for those who need to do numerical analysis. Because, among other things, in that particular area it's a language where performance is excellent, not because Python is a fast language (it's not at all, being interpreted), but a very beautiful thing about Python is that you can write its libraries in C, with bindings that practically allow you to use libraries written in C as if they were Python libraries.

And this is the trick that allowed all these tools for numerical, scientific, and financial analysis to be written in a language that's simple to grasp, even for those who perhaps aren't born developers like us. For example, think of a researcher, a scientist locked in their laboratory who can understand Python, approach programming and immediately have powerful tools available, yet the language remains easily readable and understandable. It's a perfect language, for example, for learning to program in general.

Then what else? Like our .NET languages, it obviously supports modules and packages. There's an equivalent to NuGet: PyPI, where you can now find hundreds of thousands of packages to install.

One thing that personally interested me a lot about Python when I started studying it was the fact that it was cross-platform from the beginning. It was a language that, when I started studying, was already twenty years old, so very mature. The base class library, or something like that, so it comes with a lot of included material, a bit like .NET at this point with .NET Core. Practically, whatever you want to do, there's certainly a standard way that allows you to do it.

The fact that it was cross-platform for me then was very interesting, because I came from the .NET ecosystem, which, when I started looking at Python about 10 years ago, was still absolutely out of the question. Then the world is made to change rapidly; it would also be nice if you let me tell you what happened in those years, but we probably don't have time. But fundamentally, yes, the fact that it was open source from the beginning, 20 years ago, I really liked a lot.

I must admit that in those years we fundamentally had to port our application, desktop applications, standalone, networked applications, and I was a bit frustrated by let's say the old Microsoft world, to be clear, which sounds strange coming from a Microsoft MVP, but this is also to tell why I became a Microsoft MVP after having abandoned Microsoft, I must say also quite disappointed, and I moved to the Python world. Then I was noticed in the Python world by Microsoft people, who sort of recruited me into this part of the MVP world.

Then I actually went back to doing a lot of C#, F#, in short, working in the .NET world. Actually, if I have to be honest, nowadays about 75-80% of my work is in C# and F#, and the remaining 20% is maintenance of my open-source Python packages.

So yes, let's say this: Python, personally, gave me new perspectives to answer your question. You know, when you're always inside, you always drink from the same source, you always drink the same water, and certainly it's excellent water, but you don't know the other flavors, the other tastes.

I'll give you a trivial example: in C#, historically (keep in mind that I'm a certain age, so I started writing C# really too many years ago), I remember this episode that always marked me. They had always taught me not to use try-catch if possible because exceptions in .NET were performance problems; it was a bad practice. In the Python world, it's exactly the opposite: you write code without too many guards, you focus on the logic that solves the problem, and you catch and handle errors as needed.

Going back to the C# world, I started using this thing a lot in Python and used it aggressively, even to the dismay of my colleagues who had stayed in the world. And this is simply an example. Then, in the meantime, obviously, in these 10-15 years, try-catch is no longer a problem like it was 15 years ago.

I brought some things from the Zen of Python, a kind of decalogue that Python programmers try to follow, into the C# world. For example, "Explicit is better than implicit," which is a classic of the Python world. So, rather than write one more line of code, make your intention exactly clear, rather than hiding things behind too many automagical things.

So, all these little things here. Now, yes, the .NET world has given us a lot, it's not even worth saying. Actually, now they'll do the same thing here, too. When I moved there, and especially there, I think C# was already very mature. So I found myself... I remember another thing: when, for the first time, I didn't understand how a REST call worked in Python, and I realized I could go to GitHub to see the source code of the framework I was using, which was Flask.

It's a bit like if I, 15 or 10-12 years ago, had been able to look at the ASP.NET source code to understand exactly why things weren't working as I thought they should. That thing for me was, the English would say, paradigmatic. It really opened my heart, and I understood that was the world I wanted to be in. Then you see, many of these arguments are a bit, let's say, weak today because C# and .NET are now fully open source. But better this way, thank God. A lot has changed in recent years.

__Nicola has a t-shirt I couldn't see well at first; it has the Superman logo, but it's actually an F with a hashtag, so it's an F# t-shirt. Is there a relationship between the functional world and Python, or is Python a traditional object-oriented world, let's call it that?__

Well, that's a good question. Actually, Python was born entirely and purely object-oriented. So anything you use in Python is an object, but it has a strong predisposition also toward functional programming, let's say. I have to be honest: if I want to do good quality functional programming, F# is a thousand times better than Python, but you can certainly do it.

Let's say this is probably interesting as well. I wouldn't have arrived at F# (let's say) if I hadn't gone through Python. Always for the discussions I was telling you about before, the approach in Python is to simplify things, break them down into... well, these are good practices used in all programming languages. But there's a tendency, let's say, to use functions rather than magic classes that incorporate state, for example.

In Python, it's quite common, even if not everyone does it, because, being a complete object-oriented language, you can perfectly well maintain state inside objects as you would in a C# class, in a classic way. But you will surely have noticed, and I think the listeners too, that the trend in C#, as well as in recent versions, is toward functional programming in a manner I'd say is almost impetuous, so records, immutables, many other things like enhanced lambdas, etc., etc.

So, coming back to the .NET world from Python, I became much more curious about F # than I had been 10 years ago. So yes, in Python you can do decent functional programming and organize your code in a functional way, but it's certainly a language that remains object-oriented, let's say, in its orientation.

And it's not even, I have to tell you the truth, compared to C#, which has been adopting so much from F# in the last two or three versions, Python is not making this huge effort to become functional, and in this, I have to say I quite agree. I really like the evolution of C#, especially for me, who also obviously does F#. I think I would really like also like to know how to say, I've also tried actually in some conferences to do outreach in this sense, to encourage the C# developer to go toward functional, and also to illustrate F#, the principles of F#.

But I also appreciate the fact that in the Python world, they said, "ok, Python at its heart is an object-oriented language and its focus is there, let's improve that type of paradigm. There are other languages that do well. And in the .NET world, this is very true: there's C#, and we have the enormous fortune of also having F#.

Now there's been an attempt at hybridization, let's say, or rather to bring into the C# world everything that's beautiful about the functional world, which sure is appreciable. I'm happy, I'm already using it a lot. But I think it can also create a lot of confusion for a newcomer to the language, who perhaps comes from object-oriented programming and finds themselves with many functional things and doesn't quite understand what to do.

I adore the latest versions of C#, and I'm very happy about it, but what is the specific direction of C#?

__Yes, I also have a sort of adoration for the latest version of C#, but I realize that having behind me... I started writing C# code in 1999 with Beta 1 of the .NET Framework. So I've been through all of them, so for me, the novelties are small things compared to the twenty years that have passed. I realize that the problem might be that, for a new developer who arrives today, they face, fundamentally, an almost insurmountable mountain to climb.__

That's exactly what I meant, so adding then also, let's say, this cognitive weight. One could ask oneself why can't I use a class instead of a record, for example, but the same thing, what's the fundamental difference? Yes, there are reasons, but one of the really strong things about Python is its ease of access for those starting in programming.

I've seen that Microsoft is making huge efforts in this regard, with video series on YouTube and sites to welcome people to C#. And I, in particular, who come from the world, I'm let's say with feet in both camps, so I'm well known in the Python world too, so much so that I've also done presentations where I present Python to the C# programmer and C# and .NET to the Python programmer.

Especially now that C# is finally cross-platform and open source, it becomes much more... before, it was unthinkable to talk to a Python programmer about learning C#, which was only Windows and only .NET Framework, standalone, etc. It was really unthinkable. Now some cracks are opening, I'm trying to slip in there, but it's very hard because clearly we have let's say an image, we're known as dotNetters in quotes for enterprise, for PA... and heavy stuff that's installed on Windows, the GAC, all these problems that existed in the Windows world.

Many times, making people understand "look, now you can take a Linux machine and run a web application written in C# with the same ease as you would with Node or Python" is really a message that leaves people open-mouthed, and they don't believe it, you have to show them. So the work to be done on our part is really a lot.

__You touched on Python at the beginning of the discussion, saying, if I remember correctly, you used Flask as a framework, which I assume is a sort of counterpart to ASP.NET. More or less? What relationship is there between Flask, ASP.NET, Eve and the REST world in general? And why did you feel the need to write a framework for REST for Python?__

Well, that's an excellent question. When I came to Python, there was a framework called Django, which was very widely used and very famous, and did the equivalent of a modern ASP.NET, an ASP.NET Core. But it was too complex, it was exactly the classic behemoth in the .NET style, because I'm talking about the old way, where you had to take everything that came or what you needed. What I needed was to practically implement the equivalent of a Web API application we have in the .NET world, so the controller... well, there's no concept of controllers, but it's the classic REST API concept.

So, Flask actually defines itself as a REST API, but it's not a true Web API. It's more of a .NET type framework. When I explain to C# programmers what exactly Eve is, I make this kind of comparison: imagine a Web API .NET, well, Eve gives you that with the addition that there was this attempt to make it very easy to put online when you need an API that's basically a front-end for a database, so not much business logic but CRUD operations and things like that.

So, in this sense natively, Eve, besides providing the REST interface toward clients which by the way is strongly opinionated (that is, keep in mind that when I wrote Eve it actually was born as an internal project for my company, so we knew exactly that a POST would create a record, a PUT would replace, a PATCH would modify), I didn't create a framework that lets you do whatever you want, precise choices were made about how verbs work, how modifications work.

And fundamentally, if that's okay with you, my framework probably lets you work agilely and quickly. If you don't agree, use Flask or another framework, or build your own. And so yes, I'd say the relationship is this: Flask could be, let's say, the core of a Web API. Look, it comes to mind now with .NET 6 this new interesting feature, which are the minimal APIs.

If you take the Flask homepage and look at the quick start example, it's maybe ten lines of code, and you take a snippet that Microsoft is publishing on its social media (David Fowler comes to mind on Twitter; every now and then, he posts screenshots of these minimal APIs), they're almost overlapping, it's incredible, right?

And so the work they're doing now in .NET 6 with minimal APIs is to remove from the logic let's say MVC and everything that was behind it, remove the routing and those things from verb management and then put it all in your hands so that you can make a pure API without the behemoth, without having to create a controller and so on.

So, Flask practically gives you that base that we'll now have in .NET 6. So, this, and minimal APIs are something that in my opinion can be very interesting for those who want to start using C# for example to make Web APIs, because when I came from C# I had the whole behemoth world let's say to manage and I found Flask which gave me the building blocks to build what I wanted, it was exactly the reason why I went to use Flask and Python.

So finally in .NET 6 we'll have something very similar and it's really impressive to compare Node code, Python code with Flask and .NET 6 minimal API code and see that the effort is very evident from Microsoft to make it interesting also for those coming from other stacks where all that, sorry if I repeat myself (I call it the behemoth), all that complication... so you have to have a controller, you have to have a view, you have to make a site, you have to have in short the data layer, all these affairs that certainly come from data user, among these and so on, are being somewhat thinned out to make everything lighter and it will be very interesting in my opinion.

__Exactly. One thing I noticed is that, finally, for the first time with .NET 6, the empty project template is truly empty.__

Exactly, Flask has been like that for me: you just need a .py file with your four lines of API initialization, and then a nice little function that responds to a GET, and you're done. Now we'll have this in .NET 6 too, which is really interesting to me. Hopefully, then we'll be able to make the rest of the world understand that .NET is no longer what it was 10 or 15 years ago, and here I emphasize this is the big commitment, in my opinion, the real challenge to win: communication.

But I have to say that on this I'm optimistic for another reason and that's performance, that is the performance of .NET Core, multi-framework, cross-platform are really interesting and this is the reason why I went back to doing a lot of C# actually, because with .NET Core I have cross-platform and performance that I don't have in Python and now I'm also starting to have a language, a stack that's agile and very similar to what I used in Python, what I use in Python or in Node for example. But let's not talk about Node, otherwise we'll have a classic flame war.

__Ok, in all of this, how does Electronic Invoicing .NET fit in?__

Well, Electronic Invoicing is also here, the result of my Python experience, that is, in Python I embraced open source to the point of becoming the first creator and then maintainer of some open source projects, and I saw the incredible potential that comes with letting's say, the benefits you have from making your code public.

And so going back to work in .NET (we're talking about 2014-2015, because electronic invoicing, it must be said, is something that was imposed by law, I think in 2019, now I don't remember, but actually the technical specifications were already in place for some years for the public administration world). So we had to do this thing internally.

Fundamentally, for those who don't know the product, Electronic Invoicing for .NET is simply a deserializer and serializer of electronic invoices that puts in your hands an instance of a class that represents the electronic invoice and that, very handily, also forces you to validate it according to the technical specifications. So you can, before submitting your electronic invoice to the Revenue Agency, etc., already know whether it will be accepted, identify any errors, and tell your user how to correct them. This is the version in a nutshell.

And so when we did this and I started working on this project I proposed to colleagues to try to leave it as open source because it was evidently something that would become useful certainly to a niche compared to Eve or Cerberus which is another project I have, but because meanwhile it's only dedicated to the Italian public and not to the whole planet let's say, but also certainly only to those who develop management software etc., etc.

But why not? It seemed to me an interesting little game, also because, I'll tell you the truth, it may seem a bit naive on my part, but it seemed to me the way to show and make .NET developers understand that open source, even from us peons, is perfectly possible. If you have an interesting project that can be useful, you can do it even if you come from the let's call it closed enterprise world, like that of .NET, and it seemed to me a way to give an example and encourage others to take the same step.

In short, at the beginning, it remained quiet for two or three years, and we used it only by us and four other unfortunate souls like us. Gradually it gained traction, it clearly became a very important thing when the law then imposed electronic invoicing and I must say we had the advantage, you see there too, of being a project that by then was already a few years old (it was from 2015 I think I left it open source), it was already mature enough to be adopted by those who were panicking because they found themselves with three months to implement something and so after that contributors arrived.

The thing about the whole Electronic Invoicing project that gives me the most satisfaction is the fact that there are .NET developers and it's evident from how they make pull requests and how they contribute to the code that they've never done it before, but with enthusiasm and obviously out of necessity they get to work, they throw themselves into it and they've also contributed pieces of code that have proven very important.

So in my small way, in the .NET world, what usually happens in other worlds I come from, or rather that I return to, so Python, is happening.

__This is a fascinating thing that recently happened to me too because I have several open source projects, one recently... a guy who I later discovered was Australian started opening issues, then a couple of pull requests and then more and now I'm evaluating within myself whether to make him a maintainer because he's contributing in a very important way and if the project hadn't originally been open source because it didn't need to be open source, originally there wouldn't have been all the contributions that I honestly had never thought of, they didn't make much sense.__

Absolutely, I confirm and my experience too. To give a practical example on Electronic Invoicing, a guy comes to mind who contributed... I think I implemented serialization in JSON, in addition to XML, for these electronic invoices, but I wasn't at all interested in deserialization. It's a guy... moreover, it's also the contract, the pull request arrived with this feature completely implemented, and so now I support bidirectional JSON or the famous digital signatures, which are a very complex topic.

Electronic invoices can be sent as pure XML or with a digital signature. Actually the large part of those features was contributed from the outside. They're important features you see that I didn't work on, clearly, then I contributed to quality control, everything you want, but giving me so much value to the project and obviously to the community.

And among these contributors, there are precisely new contributors who, often precisely because of their enthusiasm, are the ones who in the end contribute the most, with also those more interesting features.

If I have a minute to tell another episode that comes to mind, in Eve, there was this guy. I had already been on GitHub for 4-5 years; it was going very well, and it had widespread adoption, which I was very proud of. After which, this pull request from this guy arrives, with, I remember, something like 800 code changes, so a monster pull request. Going to look at them, they were all changes to comments, what in Python are called docstrings, they're practically the inline documentation that you put as a comment that then serves developers to understand your code.

They were full of typos and errors because I'm obviously not a native English speaker, so there were grammatical errors, typos, and other issues. It was super embarrassing because I realized that my code with all my errors had been seen by who knows how many tens of thousands of programmers, who knows how many laughs they had at my expense.

But the beautiful thing about this contribution was that he wrote to me, "look, I'm not an expert programmer, so I thought of contributing in this way. And from that day, the Eve documentation has enormously improved, so that a contribution which is not a code contribution, from an absolute non-expert for me personally, for the whole project, has had and still has an immense value.

So this is also a message, I always tell this episode. There are opportunities to contribute in a significant way for anyone, from the super programmer (the famous "10x developer" if you also say it in Italian), but also those who have just started can help and indeed, they should be encouraged because they're the ones who have so much enthusiasm, among you who then give them confidence, the problem is that after a while being a maintainer becomes very demanding and you start to delegate to someone who I'm not saying replaces you, but maybe even yes.

__In fact, the next question is precisely that: if I understood correctly, both open source projects have some relationship with your work, but obviously, the cognitive and managerial load is significantly higher than what your work would generate. So what is your experience in the world of open source governance, and in general, managing projects that start maybe a bit like, I don't know, what we could call a playground, and then explode in your hands, and you say, "oh my God, now what do I do?"__

Yes, it's a gigantic problem actually because with Eve, thank God, we've now reached a maturity and stability of the framework that allows me to live quite on my laurels, but attention, simply because I chose that the project is mature and stable, and I don't want to take it, say, to a version 2.0. If I were like .NET can be forced every year to make a new major release, it would obviously be my job 24 hours a day.

I also confess that to solve this problem I also tried to make Eve somehow profitable, to have an income from the project itself through donations, like "buy me a coffee", but not with the objective of becoming full-time living, but with the objective of being able to pay myself half a day of work per week to dedicate explosively to the project, because if I could have dedicated, say, every Friday 8 hours to open source, you would certainly have a project 10 times more beautiful than what it has now, same thing with Cerberus, same thing with Electronic Invoicing.

As you can imagine, this thing didn't have much success because everyone is very good at installing packages, but when they have to put their hands in their wallets, they're much less good at it. Maybe there was gratitude for receiving this, which is very pleasant, but the long-term strategy is missing... another topic; we don't want to discuss now how to maintain...

There comes a moment when the cognitive commitment is really great, you have so much other business and other work types to deal with, and it becomes a problem. The solution, for example, I was lucky because, a bit like what happened to you, one of these contributors, gradually, I really let him, even in a somewhat sly way, I let him take control, but it started with minimal pull requests, then he gained courage, I sort of nurtured him.

In the end when I was certain he knew the codebase very well, he was also an expert, in short fundamentally Cerberus I left in his hands 100%, so I follow it from afar, I receive email notifications, if he has some important modification to make he asks me for advice, but actually he even has the rights to publish updates and so let's say now for me I'm simply a father watching from afar the child grow, so to speak.

For Eve, I'm still the main maintainer, but as I tell you, the choice of Eve was perhaps made with the idea of being able to continue living and earning, let's say, my salary. It was ok. The product is mature. From now on, we accept pull requests for bug fixes or mature new features that make sense to incorporate, but I don't foresee further development in any direction.

Electronic Invoicing, for me, is strategic because we use it every day in the company; we ultimately make management software, so there I remain the maintainer, and I do it gladly because there's a necessity.

So, in general, hopefully in the .NET world too, we'll arrive at this... so, many have told me "how nice, I'll definitely make a donation, we'll make a donation for Electronic Invoicing because we use it in the company", I think not even one has arrived. So in this certainly the .NET world still has to mature and become aware of the fact that a long-term investment for a product you use every day and that gives you income in the end somehow (otherwise you wouldn't use it), it makes sense to think about contributing to the long life of the project to not risk finding yourself at a certain point with the maintainer who took the motorcycle and went to the Himalayas to climb and you have a critical project maybe that's no longer updated, that has security problems, etc. On this, there's work to do.

__Ok, to conclude, last two quick questions. Still staying in the open source world, if you had to give advice to someone who wants to start an open source project and advice to someone who wants to contribute to an open source project.__

Yes. So, for those who want to start, I'd say don't worry. In the sense that, as you said before, there were projects you had put open source that actually didn't need to be. "They didn't need to be open source." This is, the perception is a problem of really, I can't translate it into Italian, but it's a problem of wrong perception, in the sense that actually there's certainly someone on planet earth who has to solve the problem that you have to solve at that moment.

So even projects, if you want trivial small ones that serve little purpose, thanks to potential algorithms and tools, exposure from GitHub, from Google and so on, rest assured that if you're doing a project for electronic invoicing, someone else has that problem. So the first thing is that the history of open source is full of projects born as hobby projects, put on GitHub almost like this for convenience, because this way I have a remote backup, which actually exploded in the hands of maintainers because they were successful.

But even if they weren't successful, it serves you in the meantime to acquire the know-how, which is not small, and to gain experience in doing so and overcoming the shyness of sharing your code and showing it to the public. So, this is the other very important thing. My programming style has evolved a lot, thanks also to seeing what others do.

Sure, it can also be, how to say, sometimes not humiliating, I'd say, but certainly it puts you in your place when you see that your code has been refactored in a much more performant or more elegant way by others, but it's there that you learn. It's a bit of the discourse about always drinking water from the same place I was telling you about. So certainly I'd say first thing, don't be afraid, throw anything on GitHub even if the code is not the best... sorry... don't stay there to refine it, to clean it up, because maybe someone else will do it for you, who will even be grateful to you.

The other thing, probably, is... for those who want to start contributing instead, as I was saying before, there certainly are projects of the day that you use, even in professional frameworks... I'll also make here, I'd say, another episode. When I was preparing a talk on Python and explaining how to use Python inside Visual Studio, which few people know, you can use all the Visual Studio features you're used to to write Python code. I realized that the official documentation on the Microsoft Visual Studio site had some shortcomings in the pages dedicated to Python. And so what did I do? I made a fork of that documentation, which is now finally all on GitHub. I contributed a fix to this documentation.

And now, I don't know if it's still like this, but two or three years ago, if you went to the official Microsoft documentation for Python, you'd find my little face among the contributors. So there you go, I made a contribution even to an official Microsoft project. Free, because it's the tool that I use every day.

I'm convinced that a large part of us developers have this experience of noticing a small error, a small problem, or a specification that doesn't necessarily require an extremely complicated algorithm to solve. It can also be, as I was telling you in that other episode, a docstring, a comment with a typo. They're all experiences that add up, that help you gain familiarity with the context, and so don't start maybe by contributing a Fibonacci optimization, because I don't know what.

So, really start from the trivial, from the simple, from what you do every day, because you know it very well and you're already competent. After which, there's time and a way to gain confidence; many of these my contributors, as I was telling you, start like this. Then, gradually, they gained courage and went to examine the deeper code, to solve the more complicated issues that I myself didn't feel like going to look at, because I knew it was a hornet's nest and the willing one arrived who did it in my place, riding the enthusiasm, which maybe I don't have anymore, but they have it, the positive energy to use, to spend.

__Good, very interesting, I agree completely. It's one of the most common barriers to entering the open source world, precisely because itis tied to the idea that "I have to contribute," and you have in your head that the contribution must be substantial, when, in the end, it's often a small thing.__

Exactly. The novice contributor, let's say, is intimidated and thinks they should contribute something fundamental, but it doesn't make sense to contribute. On the other hand you have a maintainer who is literally at the window waiting for those who contribute the small things to arrive, because they're those, many small things that then are small things relatively (it's the perception of the remote developer that it's a small thing), it's all work that you take away from the maintainer and that you take away from the community.

So even the very small thing I can't wait for those more sought-after so-called small things to arrive. Actually, it has great value, as seen in the example of the 800 typos in the Eve documentation.

__I thank you for your availability. It's been a very pleasant chat. I hope to have you as a guest again, and as we shared before we started, we discussed an interesting topic that could be fitness for developers.__

If you decide to do it, call me. Thanks so much to you and your whole team for what you do with this podcast. You do an excellent job. 

__Thanks so much, thanks so much and thanks again for your availability. See you next time, hello everyone.__

Bye-bye, bye everyone, thanks.