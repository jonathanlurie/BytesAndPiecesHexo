---
title: Side project The Map Crafter
photos:
  - side-project-the-map-crafter/cover.jpg
date: 2016-03-19 20:25:41
tags:
- map
- TheMapCrafter
- project
---

I always loved maps. For the knowledge they carry, for the stories they can tell after we get to know them.

<!--more-->
![](cover.jpg)

There always was a large map pinned on the wall of my grandparents' office, I could spend quite a lot of time staring at it, basically every time I happened to walk near it! When I was about 11, they changed it for a new one. At first I didn't really like it, it just looked smaller, but then, I noticed something:

> « Where is USSR? Where is Yugoslavia? »  

Quickly, other questions started to pop into my head:   

> « What happened to this border, why is it so straight? »  

> « Pakistan, Uzbekistan, Tajikistan, why all those countries end by "*stan*"? Who started that? ».  

Because maps are not only the result of geological events and natural borders, I knew those questions would find more answers in a history book. What I see now in maps is rather a stack of past events: war, peace, colonizations, glory for some, collapsing for the others.

About six or seven years ago, I discovered [Openstreetmap](http://www.openstreetmap.org/) (osm) and its ecosystem. The osm foundation made geographic data collaborative, open source and thus, available to anyone on their website and through an [API](https://en.wikipedia.org/wiki/Application_programming_interface?oldformat=true). It was now possible to *make* maps!  

Armed with a freshly installed Linux distrib and a lot of courage, I quickly tried to write some scripts to create my own maps, with my own design. Nothing could stop me... except the storage capacity of my laptop, my limited knowledge and the lack of documentation. I kept on trying different scripts, different apps but never quite reached my goal of making my own map designs with a fine appreciation for details. At the time, it was difficult to find the right data, the right tutorial for newbies, and if by any luck you reached this point, the chunk of geo data were taking hundreds of gigabytes...  

## Why was that so important?
I really couldn't say. The only thing I know is that I wanted to create maps that people could look at and say:  

> « Look at this corner, you see just there. I had my first apartment here. It was real shit but I loved it! »

We own a city as much as it owns us. The network of streets gets revealed as long as we experience it with new people, for new reasons. Memories are developed and looking at a map brings them back. Let's give a nerdy name to this phenomenon, what about *time-space projection*?

This happened to me only when I faced a highly detailed map, and as a poster, it's not the easiest kind to find, especially with a beautiful design. I was pretty sure I was not the only one who looked for the perfect map to pin on my wall. I had to find a way to make my own, for me, and potentially for others.

## From paper to... paper
I knew quite precisely what I wanted:

  - We could read the name of the streets.
  - It would be very contrasty, mostly black and white, few gray levels.
  - It would display GPS coordinates and the name of the city.
  - Even highly detailed, the overall design must remain minimalist. That is quite a challenge.
  - The paper must be thick.
  - The ink must be matte, making velvet deep blacks.
  - The poster must be large enough to appreciate the details.

But the problem I encountered on my early steps was still there: what tools can I use? By chance, [Mapbox](http://mapbox.com) gave me the answer about two or three years ago: *Mapbox Studio Classic*, a software for making maps and tuning the design of every little element depending on zoom level. This was, of course, based on osm data. With some work, it was now possible to craft the map I wanted. Not any kind of work, not the shitty-scripts-with-packaging-hassle kind of work like it used to be. No, real programming, with a dedicated language (*CartoCSS*). For now, this would be my new toy!  
There are many great things with *Mapbox Studio Classic*: it comes with some code samples, a very well documented API and a png export feature with a decent resolution. Within the first week, I managed to get pretty satisfying results! And it was soon time to take things seriously!  

Everything started with **Manhattan**, NYC. I've never been there, though, and I never even looked at a map of NYC before, but strangely, the names reminded me scenes from movies (*« Yipikaye! »*), series (*« I'm fabulous! »*) or some documentaries about the birth of Hip-hop culture. Actually, we all know a bit of New York City! Plus, an island like Manhattan and the geometrical street network were nice features to play with.

After a first and satisfying print test, I decided to launch a shop on Etsy to share my work with other map enthusiasts: *TheMapCrafter* was born! It was also my first experience as a seller on the Internet. Frankly saying, at first, I was not convinced.

## Tangible world, tangible issues

Etsy is a great platform, no doubt about that. Of course it could be improved with a less messy user interface but the main problem to me was to deal with orders, packages and post office. Not that I've had a lot of customers but I couldn't figure how I would scale up. Actually, because of my shitty logistics, I didn't want to scale up, I knew I wouldn't have the time to handle it, pack the poster, find cardboard boxes that were solid enough... I had to figure something else, more scalable, easier to manage so that I would have more time to do what I want, like crafting maps.  

The idea was simple: since *TheMapCrafter* is a side-project, it should not cost money unless it brings money. In other words, it should sustain itself but I am not looking to get real money from it. OK, one day maybe, we'll see.  
I found several websites that handle the entire supply chain of selling prints, most of them were *community websites* with a high production cost (ie. [Society6](https://society6.com/)), almost no choice about paper or ink or even less on the web-design and all [UI/UX](http://www.webdesignerdepot.com/2012/06/ui-vs-ux-whats-the-difference/).  
What I was looking for was the *Tumblr of online store*: with somewhat of a community (with likes, follows and messages), highly customizable with a fair amount of templates to start with, and well, that interacts well with other online companies (like fine art printers and drop shipping services), and with few to no monthly charge. If I was playing *[Guess Who?](https://en.wikipedia.org/wiki/Guess_Who%3F)*, the game board would be large like Russia and I wouldn't even be sure the guy I was looking for actually exists! But _**I FOUND IT!**_  

Its name: [Tictail](http://tictail.com), a startup born in Stockholm, Sweden in 2012. Strangely, they provide everything I was looking for. (Note that I am in no way affiliated with Tictail) I don't really know how they sustain themselves since the only thing I pay is the payment platform fees (Paypal or Stripe), so it's not even in Tictail's pocket. Anyway, I was able to choose a store design, to customize it like in Tumblr and to link my account with a printing service that I can order samples from to check the quality (I will write a post on this particular point). And the cool point, Tictail's version of [TheMapCrafter](http://themapcrafter.com) has two different access points:  

1. A somewhat [independent store](http://themapcrafter.tictail.com), that I've chosen and customized the design (HTML/css/JS)
2. A [page](tictail.com/s/themapcrafter) within Tictail's community store. These all look the same (except for the cover image) but it's easier to bounce from one creator to another thanks to suggestions.  

Note that with $1.5, the *independent store* (case 1) can use a custom domain. I didn't do it yet and even though I own [themapcrafter.com](http://themapcrafter.com), it's a simple redirection.

## Here it is, but what's next?

Simple question actually. Since I found an efficient way to share my work, I can now spend some time actually crafting maps. So far, here are the maps available on [themapcrafter.com](http://themapcrafter.com) :

  1. Manhattan - remastered... many times!
  2. Paris
  3. Tokyo
  4. San Francisco
  5. London
  6. Montréal

(size: 18"x24" and 24"x36")

I have a decent list of cities I still want to design. The next stops will be Barcelona, Berlin and Warsaw (in no particular order, I still don't know).  
Since it's a part time *side-project*, it means I have some other things to take care of (like pushing the tests of my also-map-related app [Locate](http://duskr.co/locate) before I launch it!). Not that I am taking TheMapCrafter lightly, but I want to pursue it with no stress and keep making about two cities per month. I also plan to make an *outdoor series* of maps to pin on your wall!

Now you know a bit more about this side-but-quite-important project, I hope you want to virtually travel with me here, on *Bytes and Pieces* and on *[TheMapCrafter](http://themapcrafter.com)*. I will keep on posting more things about that, so stay tuned, signup to Bytes and Pieces' newsletter and follow [TheMapCrafter on Twitter](https://twitter.com/TheMapCrafter) or [Facebook](https://www.facebook.com/TheMapCrafter)!
