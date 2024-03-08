---
date: 2024-01-25T14:37:42+01:00
title: "How to fix the crontab error `rename: Operation not permitted`"
tags: ["til", "crontab", "linux", "bash"]
---
Today, something unexpected happened while I was working on one of our Linux
machines. I issued the `crontab -e` command to add a cron job to my user's
crontab file, modified and saved it, only to the following error:

```bash
crontab: installing new crontab
crontab: crontabs/<user>: rename: Operation not permitted
crontab: edits left in /tmp/crontab.hgmsOH/crontab
```

Puzzled, I checked whether my user permissions were all right, if the disk was
full, and several other things. Long story short, the fix was this one:

```bash
sudo chattr -i /var/spool/cron/crontabs/<user>
sudo chown <user>:crontab /var/spool/cron/crontabs/<user>
```

Somehow, the user's crontab file had become immutable.