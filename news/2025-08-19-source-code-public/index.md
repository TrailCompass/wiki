---
slug: 2025-08-19-source-code-public
title: Source code is now public
authors: [itoncek]
tags: [status]
---
I've decided to not hold the secret anymore. **TRAILCOMPASS' SOURCE CODE IS NOW PUBLIC!**
<!-- truncate -->
Okay that was a bit dramatic, but it's true. From now on, you can see and contribute to this project. I've decided to do this, after I saw the reaction to TrailCompass being (at least a little bit) real. The development really slowed down during the summer and I felt it was time to do something about this.

It's not looking good, I've done enough progress to be meaningful, but not enough for the app to be finished. Right now, I'm not at home and will be out of office until the start of September. Starting in October, I'll have some real world stuff, which I'll need to be fully concentrated for and I'll probably have minimal time for other projects, let alone this monolith of an application.

It might not be obvious from the premise, but running everything programmaticaly is not easy. I've hoped to have it finished by June, but looking at the calendar, I don't think I'm able to fulfill that expectation.

I guess this is enough of the fluff, if you don't want to contribute or want to wait for the final product, you can leave now. The next part of this post is only about the current state of the project.

The project is currently split into four main parts. The [`commons`](https://github.com/TrailCompass/commons) module, which glues the whole project together and defines the protocol, which all modules follow. 

The [`backend`](https://github.com/TrailCompass/backend) is the main server, which manages the state of the game in a PostgreSQL database. It is also the only source of truth while playing. 

The [`app`](https://github.com/TrailCompass/app) is the android app for interacting with the TrailCompass server. Mostly written in Jetpack Compose, the app is designed to have separate activities for all modes, but within each mode, the application should only swap contents of the activities, not the whole activity.

The [wiki](https://trailcompass.itoncek.space/) ([repository](https://github.com/TrailCompass/wiki)) *will (someday)* contain all the knowledge needed to develop, deploy and run TrailCompass events. 

That's it, read the [wiki](https://trailcompass.itoncek.space/), join the [discussion](https://github.com/TrailCompass/backend/discussions), fork and contribute :heart:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\- IToncek 