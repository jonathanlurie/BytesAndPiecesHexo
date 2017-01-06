---
title: First project locate
photos:
  - First-project-locate/cover.jpg
date: 2016-04-04 20:33:32
tags:
- code
- project
---

We all need to start somewhere, right?

<!--more-->
![](cover.jpg)

As I told [earlier](http://bytesandpieces.jonathanlurie.fr/we-are-multiple/), I am currently working on a piece of software that takes most of my time for the past 10 weeks: *Locate*. It's a kind of one-man-band since I do (and will continue to do) just about everything necessary for the creation of Locate and it's distribution by myself. In addition to being few hundreds (thousands?) lines of code, *Locate* is the **first member** of a software family I am starting: [Duskr](http://duskr.co).

So what is this all about? Good question indeed!  

## What?
Locate is a simple app for Mac OSX[^1] to help people geotagging their photos by dropping them on a map, moving some markers (to adjust if already tagged) or syncing with a GPS track. It can also be used as an image viewer with cartography in mind. That's more or less all, at least for v1.0.  
While designing the app, I did my best to maintain a very intuitive ergonomic and a rather flat and not disturbing design. Not everyone is familiar with cartography, but everyone should be able to geotag their pictures, right?

If it's about the technology involved, at the very beginning I thought I would be able to make a web app rather than a desktop app. Well, it turns out that Javascript (JS) does not play well with local files (for obvious security reasons) so I had to change my weapon. Still, making an app using web techs also meant making the UI with *CSS*, which is quite appealing compared to using QT/wxPython/Swing. And what about the back-end with all the *Exif* processing and file saving? JS on server side (NodeJS) just seemed like the right guy! If you type *```desktop app Javascript```* in Google, one of the first link you will get is [Electron](http://electron.atom.io/), a framework just for doing that, created by [Github](https://github.com/). It didn't need much time to convince me. After further testings, I was pretty glad to have chosen the path of *desktop* rather than *web*, for all the freedom it implies: no more « Do I do it client or server side? ». It can get tricky sometimes...

## Why?
Picture geotagging exists for a while now. It's not the best way of selling Locate, I admit, but what make it the app I want to use is beyond *strict geotagging* and relies more on *how to do it*. Because so far, these are the choices I had:

  1. Shareware[^2] with crappy old style design and not so intuitive ergonomic (VisualBasic, I see you!)
  2. Big and expensive machines that do millions of things and among them, geotagging (cf. Lightroom)

Speaking about Lightroom, I use it a lot and I love this software, but the *map* module is simply dumb. It does not handle *retina* display, it cannot load multiple GPS tracks at the same time, and even though it deals with timezone adjustment, the whole process is pretty slow. Plus the general ergonomic and design is not intuitive and personally I still have doubts when I have to determine if my image was successfully *found on this track* or not.

**Designing Locate was almost about taking every missing or poorly developed features from existing apps and try to make something smarter.**

## About The Features
I am not making a list here, the fastest way to get it is to go [there](http://duskr.co/locate/). But, I have to say, the one I am the proudest of is the synchronization with GPS track. Why? Because it's fast and efficient when it comes to adjusting the time delay (due to a different timezone, or most of the time, not well tuned internal camera clock).  
Also, most would say graphic design change a lot (or rather its appreciation) and follow fashion and they are right, I think the same. But I am pretty happy with the simple design of Locate and I sincerely hope that none of the users will ever need more explanation or user guide than what is provided within the app (with tooltips) or in the [screenshot web page](http://duskr.co/locate/screenshots.html). It would really mean I failed in making it simple (and did not try hard enough).


## When?
Anytime soon. The app is done, the website is done as well as the connection with services for selling Locate. What I am doing now is mostly getting feedback from friends turned beta testers. Unless I find a huge bug, Locate should be available in April 2016.

## And What's Next?
It's not because I will release Locate v1.0 that I will be done with it! Actually, I still have some features to add, and the first of them will be the *story publishing* (as a free update, because it will still be a *v1.x* ).

Meanwhile, you can subscribe to the newsletter of this very blog and follow [@DuskrApp](https://twitter.com/DuskrApp) on twitter to stay up to date concerning Locate's release!

Cheers!


<center>*Read this story on [Medium](https://medium.com/bytes-and-pieces).*</center>



[^1]: I am also working on a Windows version, but since I don't have the right equipment for proper testings, it might take a while to be released.

[^2]: Can we still use this word? Not sure.
