---
layout: post
title: Building Amazon Instant at HackTX
date:   2013-11-17 18:59:00
categories: Software
---
This weekend at [HackTX][1] I experienced my first full-fledged hackathon. I didn't have a group or even an idea going into it, but I learned a lot and came out of it with something. Check out [Amazon Instant][2]!

I ended up finding a group of a couple guys that already had an idea. The idea is almost as hard to explain as it was to build, but I'll give it a shot. They wanted to build an essay templating system that generated essays from skeletons based on some key topic. For instance, if the subject of one essay was Microsoft, you could transform it into an essay about Apple. Markov chains were mentioned (eek). It took me a little while to convince them that this wasn't the best idea. For one thing, essays tend to be tailored to the subject too closely to simply swap the subject and rebuild. Also, the fact that both essays and information sources such as Wikipedia aren't strictly structured makes the task pretty much impossible to finish within 24 hours.

Now we had to come up with a new idea. A website called [YouTube Instant][3] came to mind. I had seen it a couple weeks ago and thought it was a cool idea, and it seemed pretty simple to make. It loaded a YouTube video relevant to your search term in real-time. The creator of that site was inspired by [Google Instant][4], and I thought we could continue that chain of inspiration. Doing this was also a chance to learn how to make dynamic web pages. I looked through my bookmarks and a few candidates came to mind, including Twitter, Reddit, Netflix, and Amazon. We decided on Amazon, and the initial name was Impulse Buy. When using the site you could start with something general and get more specific as you watched the items appearing follow suit.

By the time we started making real progress, the group had shrunk to just me and another guy named Femi. Luckily, Femi had some experience using javascript. After hacking at it for a little while we were able to use Amazon's product API and AngularJS to get relevant items back as we typed. Unfortunately, there was a problem in that we would often get a bad response from Amazon. We soon found that we were being throttled because Amazon's API has an upper limit of one request per second for each API key. This was really bad for us since we were making a request every time a user entered in a new character. We turned to other website APIs, but they all either had similar limits or were bad choices for other reasons. Plus, we had already put some time into using Amazon's API.

We spent some time considering possible solutions or workarounds. We failed to find a real solution, but we did a couple of things to make it usable at a small scale. One of those things was to alternate between two different Amazon API keys with every request, giving us two requests per second. We'd probably use more than two keys if Amazon didn't require credit card information for registration. This was super hacky, but hey, this was a hackathon. The second thing we did was set a minimum interval between requests rather than query Amazon after every user input update. 600ms worked pretty well.

After a few more hours we had a site that worked for a couple people at a time, which was enough for a demo. While some groups hacked for the full 24 hours, we didn't have high expectations in terms of winning the competition, so we went home to sleep for a bit.

We met back around noon, added some polish to the site, and went on to the first round. We knew we were competing with teams of five who knew exactly what they were going to work on from the start, so winning wasn't in our sights. We did get a kick out of sharing what we'd been working hard on though.

It was also great seeing what some of the teams had created in such a short time. The first prize winners made a game like Guitar Hero, but it revolved around whistling. Another group made a peer-to-peer file sharing application that worked within a web browser.

I went home inspired to make our project better. It's kind of a bummer that it can't get any wide use because of Amazon's API throttling, but it's still cool and I learned a lot making it. Maybe one day there'll be a real workaround that makes it viable. For now, [give it a try][5], and don't worry about getting throttled; I don't get much traffic.

----
[Breezeblocks][6]


  [1]: http://hacktx.com
  [2]: http://amz.greyshi.com
  [3]: http://ytinstant.com
  [4]: http://www.google.com/insidesearch/features/instant/about.html
  [5]: http://amz.greyshi.com
  [6]: http://www.youtube.com/watch?v=rVeMiVU77wo
