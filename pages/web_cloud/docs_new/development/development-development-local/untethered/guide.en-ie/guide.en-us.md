---
title: Untethered local development
slug: guide.en-ie
section: Untethered
---

**Last updated 6th November 2023**



## Objective  

**Last updated 6th November 2023**



## Objective  

It's possible to run your entire site locally on your computer.
That way you get better performance as there's no extra latency to connect to a remote database and doesn't require an active Internet connection to work.
But it does require running all necessary services (databases, search servers, and so on) locally.
These can be set up however you prefer, although Web PaaS recommends using a virtual machine to make it easier to share configuration between developers.

If you already have a development workflow in place that works for you, you can keep using it with virtually no changes.

To synchronize data from an environment on Web PaaS, consult the documentation for each [service](../../add-services/_index.md).
Each service type has its own native data import/export process and Web PaaS doesn't get in the way of that.
It's also straightforward to [download user files](../../learn-tutorials/exporting) from your application using rsync.
