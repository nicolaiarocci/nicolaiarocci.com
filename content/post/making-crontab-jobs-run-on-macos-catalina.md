---
date: 2021-03-17T07:05:25+01:00
title: "How to Make crontab Work on macOS Catalina"
share: false
tags: ["til", "macOS"]
---
Today I learned that on macOS Catalina, cron does not work out of the box.
I know it's deprecated in favor of launchd. However, I still want to use
cron because I use it on the Linux machines I share with colleagues; it's
been part of our workflow since forever, and, well, I am a lazy old fart.

On Catalina, cron needs to be granted Full Disk Access rights. Go to `System
Preferences > Security & Privacy > Privacy > Full Disk Access` and add cron
to the allowed apps. It's located in the `/usr/sbin/` folder, which won't be
visible by default. Hit `Shift+Cmd+.` in Finder to enable hidden folders.

Remember, the cron task won't be running in your current session, so you'll
have to ensure that your scripts have the necessary rights to perform their
job. Or you take the old fart shortcut and go `sudo crontab -e`, like a boss.

Keep in mind that granting full disk access rights to cron does lower your
security barriers. Only do that if you have complete control over your system.
Of course, you can always go back and remove (uncheck) cron from the Full Disk
Access app list.

*Subscribe to the [newsletter][nl], the [RSS feed][rss], or follow @[nicolaiarocci][tw] on Twitter*

 [rss]: https://nicolaiarocci.com/index.xml
 [tw]: http://twitter.com/nicolaiarocci
 [nl]: https://nicolaiarocci.substack.com
