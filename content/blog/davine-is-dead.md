+++
draft = false
date = "2015-10-23T16:32:52.654Z"
title = "Davine is Dead"
tags = ["davine", "vine social analytics", "metrics", "analytics", "vine data", "open data"]
slug = "davine-is-dead"
ignoreupdate = true
+++

<center><sub>**NOTE:** This post subject to change.</sub></center>

### The Basics

Davine is dead. Not even three months on the new "beta v2" version and it's done already. But to be honest, we probably should've seen this coming. The model of Davine was a fully open-data and ad-free service which monitored and archived all (not necessarily *all*, but very large portions of) the activity on [Vine](https://vine.co/) - a social network from Twitter using looping 6 second videos as a medium of content creation. You can't make something survive passively and autonomously without support and Davine proved it would break the bank quickly. We were exponentially growing and could have found and archived every Vine user, post, and comment within a solid month if our pockets weren't so shallow, but the rising monthly costs forced us to close way earlier than intended.

As the graph below details, I've had to scale back our automated Vine discover process much more than I ever wanted to due to exponentially rising costs.

<iframe width="600" height="371" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/1M4EseX9QJWq7tavBTxmBNkYUEYxBaVffOwIaG7cUEiU/pubchart?oid=757586175&amp;format=interactive"></iframe>

### How'd we do?

Terrible lol. Davine was running for 10 months and 23 days on [Google Cloud's App Engine](https://cloud.google.com/appengine). If you'd like to further inspect the design or implementation of Davine, the [source code will always be available on GitHub](https://github.com/AustinDizzy/davine "go easy on me, I'm still a college student learning exactly the best way to design and implement large and scalable web apps"). All the data we've ever gathered (~20GB) will soon be available to download as both a flat CSV file and a [BigQuery](https://cloud.google.com/bigquery) dataset (this post and the project's GitHub page will be updated with links when ready).

About two months ago, I started implementing a new user fetching design. Previously, it saved all a user's numerical data into a single record with the collection of each stat being a simple array. This made things a lot harder than I anticipated as Google Cloud Datastore has a 1MB record limit. After running like that for 7ish months, I decided we'd need a change to accommodate for the new automated Vine user discovery process I wrote to grow autonomously at a quicker rate. Instead of exponentially increasing that record's time-to-write to the datastore from collecting all of a user's data into a single record, I decided to take advantage of the datastore's quick read speeds and split up all user data into an entity type. By splitting all user data over a `UserData` entity type, I was also able to take advantage of ancestors and ancestor queries to essentially link all of a user's data across the entire datastore.

The "beta v2" datastore model for a user's data looked like the following: `UserRecord --> { <-CurrentProfile, []UserData, []UserMeta}`. `UserRecord` was the record which essentially proof of a user's identity. This is the entity which is the ancestor on all other records which pertain to their user profile. The record also inherits the most recent data (both textual and numerical data) we have on that specific user. This record is updated each time we fetch the user's record from Vine. `UserMeta` contained non-numerical records if they were to deviate from a user's current record. For example, if a user changed their profile description, the change would be updated in the user's `UserRecord` to keep it current and the old description would be logged as a `UserMeta` record with the user's `UserRecord` set as an ancestor key. `UserData` contains all numerical data about a user recorded at a given point in time (a typical 24hour fetch schedule from initial discovery) (e.g. loops, velocity, posts, revines, followers, following, etc.).

At the beginning of "beta v2", I implemented a [StatHat](https://stathat.com "great service, btw") logger to save various meta stats about Davine operations. From that point on I began to collect stats about Davine's performance and efficiency. You can see by the graphs below when I tuned back our automated Vine discovery process(es) to adjust for exponentially increasing costs. Had I left them at their original settings (and actually turned them up like I intended on), Davine could be discovering upwards of 15k+ users and their activity per 24 hours.

Another interesting number here is the amount of posts to be analyzed: 7,527,742 posts across 201,601 Vine users.

<iframe width="600" height="371" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/1M4EseX9QJWq7tavBTxmBNkYUEYxBaVffOwIaG7cUEiU/pubchart?oid=2081999501&amp;format=interactive"></iframe>

### Looking forward

Davine has been through a few iterations since davine.co was purchased. At first, the goal with Davine was to [allow desktop interactions before Vine was available on the web](http://davineblog.tumblr.com/post/55670644385/welcome-to-davine) at vine.co. We took a few approaches, including a mobile browser app / extension and a node.js powered web-client.

<sup><sub>*(images below recorded 2+ years ago)*</sub></sup>
<blockquote class="imgur-embed-pub" lang="en" data-id="a/bc9jv" data-context="false"><a href="//imgur.com/a/bc9jv">early Davine screenshots</a></blockquote><script async src="//s.imgur.com/min/embed.js" charset="utf-8"></script>

Davine was only in its infancy before the shutdown, so the only things implemented publically were accruing single-user metrics and statistics. However, it was also built with the idea to monitor single posts for the nature of their comments (using [IBM Watson's Text Analysis APIs](https://developer.ibm.com/watson/)) and post growth, giving users interactive realtime graphs for their posts - almost like YouTube's video analytics tools given to YouTube Content Creators.

The basis is that Vine is both a social network and a content creation network, just like YouTube (even if the videos are at max 6 seconds). Content creators and advertisers interested in sponsoring original content should be able to see the growth of all their content and their brand image on Vine.

Maybe Vine already does this internally - it sure would be easier - and only allows certain creators and brands to have access to the tools. After all, their job descriptions have included things relating to building internal product data analysis tools and they're current hiring more [data scientist(s)](https://vine.co/jobs/olLI1fwz). But I believe social networks and content creation platforms like Vine need these tools available to the public. They'd provide large datasets for researchers to learn from and conduct studies on. Especially a platform like Vine which is used by both a growing number of millennials and has enough corporate-sponsored content.

Anyways, for a true looking forward conclusion, Davine may or may not be dead. I don't believe it's worth the costs due to extreme lack of project traction, so it's on the back burner for now. I may or may not pick up on it down the road and work on designing it to run cheaper, more efficiently, and through a proper engineer's approach instead of just hacking a bunch together.
