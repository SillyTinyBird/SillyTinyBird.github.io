---
layout: post
title: "Alt3r Rooftop Run: Generation"
date: 2023-06-10
description: Contract work (in team of 3)<br>Game developer (Unity, C#)
categories: ["project", "finished", "unity", "mobile"]
image: /assets/post_content/wfPreview.gif
---
> Source code for this project can be found here: [Github](https://github.com/SillyTinyBird/AlterRooftopRun)<br>
> You can play the game here: [GooglePlay](https://play.google.com/store/apps/details?id=com.SillyTinyBird.AlterRooftopRun)

At the heart of Alt3r RooftopRun is the level generator. 
To ensure endless gameplay, it has to be reliable, but also flexible enough to provide the player with fun and never repeating challenges.

Generator is working on the wave function collapse algorithm, which is inspired by the [marian42 implementation](https://marian42.de/article/wfc/).
I used Unity's ScriptableObject as a container for my prototypes, which in hindsight was a terrible decision because it got messy really quickly. In retrospect, I should have used a json file for this.

![shapes]({{site.baseurl}}/assets/post_content/shapes.png)

Early tests were made with only 7 shapes (excluding their rotations).
Here's canvas build by wave function collapse algorithm. In this example i forgot to allow prototypes to be neighbors with themself. 


![result]({{site.baseurl}}/assets/post_content/bigShapes.png)


The level itself is separated on two interchangeable chunks, while you are running on one, the other is generating. Heres how it looks with height of 3 and length of 40:


<center>
<iframe width="560" height="315" src="https://www.youtube.com/embed/FTUBILfYu34" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</center>


The game used 21 images and the collection has 47 prototypes in it. The difference is that there are a bunch of prototypes that are only used to make sure that the generation doesn't brake.

![buildings]({{site.baseurl}}/assets/post_content/buildings.png)

This configuration of the wave function collapse algorithm with gameplay elements like obstacles and trampolines (to get to the upper or lower level) is doomed to have critical sections, like right after the trampolines, to make sure the player doesn't bump into an obstacle while the animations are playing.
To ensure reliability, I had to make a bunch of prototype plugs just to keep things working. It was tedious, but the result was worth it.

Once again, you can play the game here: [GooglePlay](https://play.google.com/store/apps/details?id=com.SillyTinyBird.AlterRooftopRun)

Thanks for reading.<br>
Maxim.
