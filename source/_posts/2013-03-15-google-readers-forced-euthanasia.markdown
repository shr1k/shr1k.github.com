---
layout: post
title: "Google Reader's forced euthanasia"
date: 2013-03-15 12:41
comments: true
categories: ["Google"]
---

Like many others, I was pretty badly struck in the face by the announcement of the Google reader shutdown.

Since I'm a techie, but not really a developer, a lot of the other Google properties being shut down hadn't impacted me as much.

However, a majority of my Internet content consumption is driven by Reader, which is why it was utterly baffling that the reasoning given was "[usage of Google Reader has declined](http://googlereader.blogspot.co.uk/2013/03/powering-down-google-reader.html)", especially given some of the [rough userbase data](http://www.buzzfeed.com/jwherrman/google-reader-still-sends-far-more-traffic-than-google) that have [popped up](http://googlesystem.blogspot.co.uk/2013/03/google-reader-data-points.html). I wonder where Google gets their data from.

### Embrace, extend, extinguish

RSS is a great content consumption protocol that is fully open and interoperable. Despite the ["+isation" of Reader (or The Great Reader Redesign)](http://techcrunch.com/2011/10/20/google-reader-getting-overhauled-removing-your-friends/) (or maybe in part *because* of it), I had assumed Google would remain committed to at least maintaining Reader, even no resources were being thrown at improving it. Especially since they had thrown their weight behind [PubSubHubbub](http://code.google.com/p/pubsubhubbub/), and bought FeedBurner. (Embrace!)

But having done this, Reader then essentially crowded out the entire market for RSS readers by just existing as a Google gorilla. For the most part, it appeared to be good. I was a staunch user of Bloglines for the longest time, until it stagnated, and then I played around with a few offline readers before jumping ship to Reader. Reader was the exciting new player -- constantly innovating, adding new features, being fast to load, and with a great mobile interface. This went on till it effectively powered most of the popular "alternative" readers (Reeder, FeedDemon, Feedly) that relied on its (admittedly undocumented and private) API. (Extend!)

But now, it appears to me that the real reason for pulling the rug out form underneath the many millions of users was the second one they mentioned, saying "as a company we’re pouring all of our energy into fewer products". This unfortunately smacks pretty hard of Google trying to dictate the direction of the web by trying to foist Google+ onto everyone. (Extinguish!)

### What's next on the block?

Given that [in the same announcement](http://googleblog.blogspot.co.uk/2013/03/a-second-spring-of-cleaning.html), they also announced that they're killing off CalDAV API access to favour their own proprietary Calendar API, I can't help but agree with The Guardian tech blogger Ruper Goodwin:

> The corporate surprise adds to the decision itself to paint a picture of a company dangerously adrift from a real understanding of its audience, and the information ecosystem.

What I just don't get is that Google serves up ads perfectly fine when people use FeedBurner, and now they're killing off the biggest FeedBurner client? They've already killed its API, and the FeedBurner site still carries the pre-Google+ design. This clearly points towards them killing off FeedBurner as well. It's more or less official -- Google hates RSS.

### The alternatives

Most people are suggesting Flipboard and Feedly as alternatives, but they either really don't get it, or their needs have diverged from the usual RSS reading crowd.

I detest things trying to learn my preferences, because my reading preferences change all the time. Sometimes I ignore a feed for 2 weeks, then catch up on all of it. Sometimes, I read every item from a source every time it's published. I don't want my preferences shaped by algorithms, as it always feels like I'm missing out on something. This is als why I pretty much **never** touched the "Sort by magic" option in Google Reader.

Additionally, magazine and river style just don't cut it. I'm not reading a magazine or a social news site -- what I need is an inbox of site updates. Whether the source is a news site, personal blog or webcomic is irrelevant, I just want to see how many updates are there, and which ones remain to be read. And horror of horrors, if I don't want to read something, I just skip it! I would prefer to not have the cognitive load of figuring out which was the last XKCD or Penny Arcade post I read, and how many I have missed over a period of being offline or plain busy. [Dave Winer is missing the point](http://threads2.scripting.com/2013/march/goodbyeGoogleReader) -- even though the tool may be called a "news reader", it really is an "RSS reader".

The RSS reading alternatives doing the rounds currently are [NetVibes](http://www.netvibes.com/), [Bloglines](http://www.bloglines.com/) (which is now just a skin of NetVibes), [The Old Reader](http://theoldreader.com/), [NewsBlur](http://www.newsblur.com/), and self-hosted options like [Tiny Tiny RSS](http://tt-rss.org/) and [selfoss](http://selfoss.aditu.de/).

Or I could get off my lazy behind and attempt to build my own. The only problem with that is that I'll probably end up hosting it on App Engine. Argh!
