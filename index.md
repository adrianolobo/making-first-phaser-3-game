---
title: Making your first Phaser 3 game
subtitle: Part 1 - Introduction
date: 20th February 2018
author: Richard Davey
twitter: photonstorm
---

![image](tutorial_header.png)

Welcome to our first tutorial on Making a Game with Phaser 3. Here we will learn how to create a small game involving a player running and jumping around platforms, collecting stars and avoiding baddies. While going through this process we'll explain some of the core features of the framework.

### What is Phaser?

Phaser is an HTML5 game framework which aims to help developers make powerful, cross-browser HTML5 games really quickly. It was created specifically to harness the benefits of modern browsers, both desktop and mobile. The only browser requirement is the support of the canvas tag.

### Requirements

[Download this zip file](/tutorials/making-your-first-phaser-3-game/phaser3-tutorial-src.zip) which contains each step of this tutorial in code and the assets that go with it.

You need to have a very, very basic knowledge of JavaScript.

Also make sure you go through the [Getting Started Guide](/tutorials/getting-started), it will show you how to download the framework, set up a local development environment, and give you a glimpse of the structure of a Phaser project and its core functions.

If you've gone through the Getting Started Guide you will have downloaded Phaser and got everything set-up and ready to code. Download the resources for this tutorial and unzip them into your web root.

Open the `part1.html` page in your editor of choice and let's have a closer look at the code. After a little boilerplate HTML that includes Phaser the code structure looks like this:

```
var config = {
    type: Phaser.AUTO,
    width: 800,
    height: 600,
    scene: {
        preload: preload,
        create: create,
        update: update
    }
};

var game = new Phaser.Game(config);

function preload ()
{
}

function create ()
{
}

function update ()
{
}
```

The config object is how you configure your Phaser Game. There are lots of options that can be placed in this object and as you expand on your Phaser knowledge you'll encounter more of them. But in this tutorial we're just going to set the renderer, dimensions and a default Scene.

An instance of a Phaser.Game object is assigned to a local variable called `game` and the configuration object is passed to it. This will start the process of bringing Phaser to life.

_In Phaser 2 the `game` object acted as the gateway to nearly all internal systems and was often accessed from a global variable. In Phaser 3 this is no longer the case and it's no longer useful to store the game instance in a global variable._

The `type` property can be either `Phaser.CANVAS`, `Phaser.WEBGL`, or `Phaser.AUTO`. This is the rendering context that you want to use for your game. The recommended value is `Phaser.AUTO` which automatically tries to use WebGL, but if the browser or device doesn't support it it'll fall back to Canvas. The canvas element that Phaser creates will be simply be appended to the document at the point the script was called, but you can also specify a parent container in the game config should you wish.

The `width` and `height` properties set the size of the canvas element that Phaser will create. In this case 800 x 600 pixels. Your game world can be any size you like, but this is the resolution the game will display in. 

The `scene` property of the configuration object will be covered in more detail further on in this tutorial.