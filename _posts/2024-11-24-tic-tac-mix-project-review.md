---
layout: post
title:  "Tic Tac Mix : a project review"
date:   2024-11-24 13:30:00 +0400
description: Talking about why and how this project went, and possibilities around updates.
categories: game review
---

# Introduction

As this first project review (can't call that a post-mortem because as a game dev necromancer, I always end up reviving old projects), I will talk about one of the most recent projects done for a 2 weeks group assignment.

To give a little bit of context, I'm in my 3rd year of studies at a training center. Since the beginning of the year we had two assignments already (including the one we will talk about in this article) as well as a third one currently ongoing as I'm writing this.

# What is "Tic Tac Mix"?

**Tic Tac Mix** is a game, available on [itch.io](https://luckiusdev.itch.io/tic-tac-mix), is a **2-player local multiplayer party game** with a childish ambiance where you play against another player in a game of Tic Tac Toe, but with the twist that each square holds a random minigame that you need to win in order to place your symbol (square or circle).

# "Why" is Tic Tax Mix?

## Game Development Process
Because it's an assignment, the genre was imposed as well as two other constraints being the local multiplayer and the minimum amount of minigames being at 3. It was also asked of us to make minigames with high replayability. 

As for the engine, we chose Unity because it is the engine everyone was the most familiar with.

## My Contributions to the Game
For the game, we ended up with 10 minigames total, with 9 of them being planned at the start of development. I made about 4 minigames (**Tanks, Mystery Doors, Splat Attack, Targets**) as well as the main menu and the **Tic Tac Toe** game. One other classmate did assets and coded the majority of the remaining minigames, and [WolfInBox](https://wolfinbox.bsky.social), former classmate and the love of my life, also did a bunch of assets as well as the Arm Wrestling minigame that I later refactored a little to use the new input handling system I coded afterwards.

![](https://i.imgur.com/gb2ezsW.png)

# Showcasing Our Game

Our head teacher proposed the class to attend an exhibition where they would present our school to various middle and high school students. We had computers to put our games on and let the people come by and play our games.

It was a really nice experience, even though it was really hot inside (as well as outside don't get me wrong) and we even ended up soaking wet when going back home. This has enabled us to do free playtesting sessions where we even gave people a **QR code** that would redirect them to a **Google Forms** after their session to give their opinion and suggestions for the game.

![](https://i.imgur.com/zzJhslU.png)

Before talking about the results of this form, I need to talk about an equally sad and funny situation about our game : the main menu kinda suck. I say that because, I saw a lot of strong reactions when some of these students passed by the computer, with a subtle curious look followed by an heavy backtracking by seeing the main menu.

As we did a group discussion about how the event went, our teacher suggested that maybe it was because of the paper look making them feel like they were about to play a boring educative game or even that it made them think of work which as you may guess, may be not the best. I get along with that theory and I can also add that the fact that the game being in English wasn't helping, considering that we are French.

![](https://i.imgur.com/E6Sr77w.png)

But for the people that played it, they seemed to really enjoy their experience and the form show that they think the game is pretty cool! We had suggestions to improve or fix the game, mainly regarding the input.

One day before the exhibition, I implemented controller support to the game. We found a bunch of bugs, and I fixed most of them, but forgot to give the fixed version to the classmate who has brought the games the day the event took place, and I couldn't do a build before I had to go. This led to people using the controller to switch to the arrow keys for the hopscotch minigame because I couldn't implement Unity's Input System due to the way it was coded by my classmate, or the controller being able to control the player 1 cursor in the Tic Tac Toe (which was one of the things I fixed in the version I forgot to bring).

There was also a bunch of people struggling to understand some minigames, and they would often do a tie or lose, because the game was in English in a room full of French people and also because we didn't give enough time to let the players read the instructions. I also did a little oopsie in one minigame, by switching the up key by the interaction key, which would led to people lose the minigame by accident...

When people understood however, they thought it was fun, so I'm pretty happy about that.

# What Happens Next?

Thanks to this playtesting experiment, we now know how to improve the prototype. First thing I did is to **improve once again the input handling system** and to centralize everything. The new system allows for both players to play with controllers, I just need to find a way to make the player 1 use the *arrow keys* instead of *W/A/S/D* when player 2 is using a controller.

To fix the comprehension errors about how to play the minigames, I will also implement a new tutorial scene in between the main gameplay and the minigame one to show a little gameplay video, as well as interactive input prompts to give the players more information and also give them the control onto when to start the minigame.

![](https:/i.imgur.com/zbSAAKP.png)

For some of the more complex minigames, we also have plans to ease the player experience to increase the chance of having a winner (e.g. changing the doors color in **Mystery Doors** once opened, adding a health system in **Thief!**).

Those fixes and QoL additions would lead to a much nicer experience, which will then enable us to add even more minigames to create unique matches.

# Conclusion

There's a bunch of things I didn't talk about, like the code, but I guess I can always make new articles to deep dive into other stuff later. Since I'm working on another assignment project and other personal ones, do not expect immediate update releases. In the meantime you can always take a look at the game [here](https://luckiusdev.itch.io/tic-tac-mix) :

<iframe frameborder="0" src="https://itch.io/embed/3108132?border_width=5" width="560" height="175"><a href="https://luckiusdev.itch.io/tic-tac-mix">Tic Tac Mix by Luckius, JoltL</a></iframe>

Thank you for passing by… ~ Luckius ❌⭕