---
date: 2021-07-14T07:05:25+01:00
title: "Will .NET 6 Minimal APIs turn heads?"
share: false
tags: ["dotnet", "programming"]
---
I am pretty excited about the [Minimal APIs][3] feature that is coming with
.NET 6. Three lines of code will be enough to build a fully functional REST
microservice[^2]:

    var app = WebApplication.Create(args);
    app.MapGet("/", () => "Hello World!");
    await app.RunAsync();

If you're a seasoned ASP.NET MVC/WebApi developer, the snippet caught your
attention because, pre-.NET 6, achieving the same result will have you messing
with a lot of extra cruft[^4]. I suspect, however, that this feature is not
primarily targeted at existing .NET developers. Developers new and old looking
at .NET for the first time, or those like me returning after a long break;
these are, I think, the designated audience. 

A long time ago, I left C# and .NET behind *precisely* because I had to write
REST APIs, and back then, the options available in .NET were, to put it mildly,
cumbersome. Admittedly, there were other reasons for switching, like .NET not
being cross-platform - I wanted to run my APIs on Linux - and general
dissatisfaction with the Microsoft ecosystem. Long story short, I went with
Python. Check out this snippet from Flask's renowned [Quickstart][1]:

    app = Flask(__name__)

    @app.route("/")
    def hello_world():
        return "<p>Hello, World!</p>"

Launched with the compelling motto 'web development, one drop at a time' and
presented as a 'micro' web framework, Flask immediately caught my attention[^5].
Cruft-free and elegant APIs are not a Flask (or Python, for the matter)
exclusive. A Node code snippet for a REST API would be similar. Now, with NET
6 Minimal APIs, we're finally matching the industry standard for code clarity
and simplicity. Moreover, .NET has better performance[^6] and strongly typed
languages that offer excellent type inference (F# reigns supreme there, with C#
catching up nicely.) I'd dare to say that the C# snippet is a winner. I mean,
look at that inline lambda, with no casts!

Minimal APIs typical use-case is everyone's favourite, microservices. I do not
doubt the delivery[^7][^8]. The challenge, I think, is the actual adoption rate.
Whether veterans will adopt them or not (over time, they will) is relatively
significant, I guess. The critical question is, will Minimal APIs succeed in
attracting new developers to .NET? 

That will mainly depend on communication. Will evangelism be robust, persistent
and persuasive enough? That's the tricky part. Every time I speak to the Python
or JavaScript crowd, I  am amazed that the majority don't even know that .NET
is now open-source, cross-platform, and blazingly performant. Most, if not all,
are tied to the old idea of a Windows-only, cumbersome, black-boxed,
enterprise-oriented offering. That's not the case anymore. .NET is on par with
the other cool stacks or is getting there very rapidly. I am afraid it's just
a little bit too late for the vast majority of the web development crowd to
take notice. It will take an enormous, coordinated effort to bring the message
across.

With the platform now ready, effective communication, branding, and evangelism
will eventually change the tide. Tutorials, getting-started guides, conference
talks, YouTube videos, and workshops should all be explicitly conceived for new
developers. The process started already. The observant can see the numerous
efforts being made in this area. Will it be enough to attract new crowds? It is
a hard bet, but I sure hope so because C# and F# are great languages, and NET
6 is modern, robust,  feature-rich, and powerful enough to go at war, and with
no fear.

