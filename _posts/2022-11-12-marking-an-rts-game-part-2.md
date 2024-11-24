---
layout: post
title:  "Making an RTS Game - Part 2"
date:   2022-11-12 21:58:00 +0400
description: Minimal update on world generation, cursor animations and code refactoring.
categories: game update
---

**NOTE: This article was ported from [tumblr](https://www.tumblr.com/luckiusdev/700738094523203584/making-an-rts-game-part-2)**

Hello again! I'm here to share some progress about my untitled cute little real-time strategy game. Before starting, if you want more info on that I redirect you to my first post and the [itch.io page](https://luckiusdev.itch.io/skulls-n-flowers) for the game!

# 1. Code Refactoring
First order of business, I did some code refactoring. "So soon?" you might ask, well yes because it was MESSY. I deleted and cleaned up a few scripts, and you know I'm thinking "whatever, the game was far from playable anyway", because it is.

There's no real gameplay yet, just snippets of gameplay elements. And that's okay for now. I know what I've already done works.

As seen in the previous post, there is a functional system of building on a grid. I also have a unit selection system but I'll talk about that later. I have removed all unnecessary code and the vast majority of the interface.

# 2. New Cursor
Nothing major, but I started coding something to add custom mouse cursors using the Cursor class from Unity. It's extremely barebones and I'll come back to it later to make it more flexible but it does the job for now.
I took inspiration from CodeMonkey's Mouse Cursor System PRO asset and from there I'm going to build my own script to come up with a flexible system that I can use later elsewhere, because unfortunately I can't afford the $40 price tag.

![](https://64.media.tumblr.com/a10ced57d5e4d2a133fdeeec55bb4271/ccc3328896a853c8-bf/s640x960/808eb288efe33345a347cc8757a03978a15bb416.pnj)

# 3. Character Customization
One of the gameplay mechanics that I like the most in this project is the possibility to customize your character or leader as I call him. For the moment, in theory, most of the customization is purely cosmetic except for the character's body, which also corresponds to the character's class (among 4 main classes that are shared with the other units: barbarian, knight, mage and ranger).
This choice will have some importance because choosing a class will grant buffs to some units, debuffs to others and will change the attacks and abilities of your leader, which will allow the player to choose his own play style or encourage replayability by encouraging to try all classes and creating unique heroes/leaders for each game.
For now and until the initial release of the game, there will only be these 4 classes for two reasons:

1. It allows to lighten the implementation of everything around this mechanic.
2. The Kay Lousberg asset pack that I use (Dungeon Pack) only had these 4 characters.

<iframe width="540" height="303" src="https://www.youtube.com/embed/nJygrd_Gcu0" title="RTS Game - Character Customization Test Scene" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

With that said, I can present you the temporary menu to test this famous character customization.

For the moment, it has no effect on the gameplay (obviously, nothing is implemented yet) and the character is not saved, but I'm quite satisfied with the result.
I still need to add the possibility to remove the hat and the hair, as well as to manage some edge cases like the fact that the knight's head model is directly provided with hair unlike the other heads.

# 4. World Generation Overhaul
The biggest thing I did (while writing this devlog post) is overhauling the terrain generation. For that, I followed IndividualKex's "How to make a procedural grid world in under 2 minutes in unity" series. (Side note, he's a very fun guy, check out his channel)

The generation work, I had a little trouble with the generation of the edges of the island for a moment but that's fixed now. The system also generates trees and I also plan to generate the rest of the resources afterwards, of course. 

# 5. Conclusion
The next step will be to re-import everything on a new Unity project to be able to use the Universal Render Pipeline (I want to die) to make the game more beautiful afterwards. As I didn't implement a lot of stuff, I don't find it extremely problematic even if obviously Unity projects take a lot of space (I really don't understand why).
I think I could have used Godot, since it is my engine of choice for my projects. However, I'm going to continue to code this game in Unity because I find that it's more suited to my needs for this project, and one of the goals is to show what I can do to a school that I want to join (and that by extension "focuses" on, or at least uses the Unity game engine as a main tool for learning). I'll make a new devlog in a few days to show you the progress of the project, porting to a URP project shouldn't take too long.

This is all I have for today folks, thank you for passing by… ~ Luckius 🌼👑