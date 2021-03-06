---
published: true
title: Agile Architecture by QWAN
layout: post
tags: [architecture, DDD, eventsourcing, CQRS, hexagonal, xpdays]
categories: [Conference]
---

On the evening of the first day of [XP Days 2016 Benelux](http://www.xpday.net/2016/), there was an unofficial track where [Rob Westgeest](https://twitter.com/westghost) and [Marc Evers](https://twitter.com/marcevers) from [QWAN](http://www.qwan.eu/) wanted to do a dry-run of a future presentation.
This session started at 9pm and ended at 10.30pm :-) 
I had planned to go to my hotel after dinner and blog about my experiences during the first day, but during dinner I had an interesting talk with Rob and I decided I wanted to see the dry-run.

Their talk was about a project that consisted of a monolith <!--more--> java codebase.
It was hard to add features or implement changes, the domain was pretty entangled.
The domain entities were representations of the database and they bubbled upwards through the architectural layers.

They told us how they did a rebuild in about 18 months with about 20 FTE's.
During that time they kept the old system running but froze all new development.
Eventually, the old system was replaced with a big bang.
They relied heavily on concepts like DDD, Event Sourcing, CQRS and Hexagonal Architecture.
I've listed some findings about them that I found interesting or wasn't yet fully aware of:

* DDD: if you have a concept that exists in more than one subdomain, this concept should get separate storage per subdomain.
* Event Sourcing: choose things that have a short lifecycle in your domain (e.g. an order vs a customer). 
* Event Sourcing: business events are more stable than the domain model. 
* CQRS: events were propagated to an indexer and went into an Elastic search store. This served as the source for querying the read model / doing projections.
* Hexagonal Architecture: with a layered architecture it's easy to end up with a domain that depends on the DB / Hibernate. Thinking in terms of ports and adapters steers you away from this pitfall.

It was nice to hear how the use of ES and CQRS helped to turn this project into a success.
Great job QWAN! 