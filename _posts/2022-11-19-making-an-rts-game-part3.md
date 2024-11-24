---
layout: post
title:  "Making an RTS Game - Part 3"
date:   2022-11-19 18:22:00 +0400
description: Procedural generation updates, A* pathfinding, unit formations and path smoothing.
categories: game update
---

**NOTE: This article was ported from [tumblr](https://www.tumblr.com/luckiusdev/701358689289928704/making-an-rts-game-part-3)**

Hello ! Here I am once again to talk about my game. This time, less things done overall however some interesting topics I will talk about.
This part will be dedicated to the movement of the units on the map.

# 1. "Optimizations" on procedural generation
But first, updates about terrain generation!

This is not really an optimization, but in order to generate the whole map, I had to cut the mesh in several small pieces, more commonly called chunks. Indeed, I learned the hard way (by smashing my head for 1 hour before getting the answer) that the number of vertices for each mesh in Unity is limited to 65535 (vertices).
Let's do a quick calculation:
If I generate a 100x100 tile map, then there will be 10.000 total tiles on the map. With 4 vertices per tile, this gives us 4 * 10.000 = 40.000, so far so good.
However, if I generate a map of 150x150 tiles, we have 4 * (150 * 150) = 4 * 22.500 = 90.000 vertices!
And so, here is the problem. Once identified, I could start working on the "chunking system" a.k.a. creating several small meshes of a certain size (for example, a chunk of 10 tiles each) and placing them in the right place. So each chunk is only 10*10*4 = 400 vertices.

Everything worked the first time as you can see…

![](https://64.media.tumblr.com/e40eb7f1277f0c9d03aa5243e49185a9/aad74b16d6a34a38-12/s640x960/1be69eee4d3d8f2b83de6f725d01267827498b7e.pnj)

But I finally got everything working after a few (long) hours of work. Here is the initial result:

![](https://64.media.tumblr.com/781088ec611f23519d5fd704b3747b9c/aad74b16d6a34a38-94/s640x960/2ac1e6b2141fea8dfed3377b7ca0d6d6d4f0afd1.pnj)

And the updated version with much nicer colors (and addition of sand tiles, a pain in the ass, also) :

![](https://64.media.tumblr.com/350ec16ad2681e933f948f60a3a033ad/aad74b16d6a34a38-a5/s640x960/00e16e148da4c0fb5a4f5854d140f3596efd4508.pnj)

The next thing to do to further optimize it is to do m u l t i t h r e a d i n g, but that will be for later.

# 2. A* Pathfinding Algorithm
As I can't use Unity's native NavMesh system since I generate the world procedurally (or I would have to do more research about it), I needed a way to move my units on the map while avoiding obstacles. The solution is simple: the A* Pathfinding algorithm. I'm not going to talk about it in detail, because people much smarter than me are already doing it: [watch this Code Monkey video](https://href.li/?https://www.youtube.com/watch?v=alU04hvz6L4).

<iframe width="540" height="303" src="https://www.youtube.com/embed/alU04hvz6L4" title="A* Pathfinding in Unity" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

It's a bit complicated to see but you can see the green line that corresponds to the path the entity will take.

![](https://64.media.tumblr.com/1efa9eb6376ccd4ec94ccc6f04a0a81c/aad74b16d6a34a38-86/s640x960/49ab033809534830fa70319f1f5070055185ee05.pnj)

And here, a small clip to see everything in action.

![](https://64.media.tumblr.com/271e024da0ce9bb4f61f2ad7350d804e/aad74b16d6a34a38-53/s640x960/4cc4da6414b04072f979e42525324ac8736b1668.gifv)

# 3. Path smoothing with Chaikin's Algorithm
**NOTE: Links are dead :(**

At this point, the unit can move on a path to the chosen destination but the path is rather… linear. I wanted to find a way to round out the path.
So I inadvertently (or by a divine message) discovered a site that showed me the [**Chaikin algorithm**](https://href.li/?http://graphics.cs.ucdavis.edu/education/CAGDNotes/Chaikins-Algorithm/Chaikins-Algorithm.html). A little more research and I was able to find another site that detailed [how the algorithm works](https://href.li/?https://www.bit-101.com/blog/2021/08/chaikins-algorithm-drawing-curves/).
With that, I was able to implement it and round the sharp turns along the way.

![](https://64.media.tumblr.com/2587c2f8709964abde0ef8db56ccaa9d/aad74b16d6a34a38-8c/s640x960/ca59703bc666d2a27ba06250d26e96364874e601.pnj)

As you can see, the path is much smoother, as the algorithm adds extra points to round everything out.

# 4. Unit Formation
And finally, I started implementing what we call unit formations. This is simply placing the units in a certain way, more generally in a grid. For this, I was once again able to rely on an amazing [tutorial from Tarodev](https://href.li/?https://www.youtube.com/watch?v=NEFxWkTRVCc) that explains how to implement this concept.

<iframe width="540" height="303" src="https://www.youtube.com/embed/NEFxWkTRVCc" title="Army Formations in Unity" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

I slightly modified the code to allow the addition of an offset, which allows me to move the center of the formation to the mouse position. As you can see below, the units move to a selected point in the formation.

![](https://64.media.tumblr.com/28375db1259fb82c87419525b3e11cd4/aad74b16d6a34a38-c6/s640x960/75ca2b7e626c723c2c04a526bdbe8a3844d4ee3a.gifv)

Thinking about it, I don't really like this system and it doesn't look very organic, and I'm thinking of changing to a simpler system where the units move to a random point within a radius of the chosen point, which will allow me to take advantage of the implementation of the **Poisson Disk Sampling** algorithm I coded (copied) earlier for an old project (damn, it takes a lot of algorithms to make a game…).

I'm also thinking of trying to implement the concept of boids to make the movement of units even more unique, as well as avoiding unintended collisions between them. But I'm going to focus on the essentials first, and the next step will be to implement the first bit of gameplay: harvesting resources.

If you want some info between these posts, I recommend you to follow me on [Mastodon](https://mastodon.gamedev.place/@luckiusdev), [Bluesky](luckiusdev.bsky.social) and even [Twitter/X](https://x.com/luckiusdev) (as long as the latter exists) where I post from time to time what I'm doing. Again, since I don't have access to my computer during the week, progress will be slow but I'll do my best to propose things as time goes by.

On that note, see you next time! ~ Luckius 🌼💀