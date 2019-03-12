---
title: Making your first Phaser 3 game
subtitle: Part 9 - A score to settle
date: 20th February 2018
author: Richard Davey
twitter: photonstorm
---

There are two final touches we're going to add to our game: an enemy to avoid that can kill the player, and a score when you collect the stars. First, the score.

To do this we'll make use of a Text Game Object. Here we create two new variables, one to hold the actual score and the text object itself:

```
var score = 0;
var scoreText;
```

The `scoreText` is set-up in the `create` function:

`scoreText = this.add.text(16, 16, 'score: 0', { fontSize: '32px', fill: '#000' });`

16 x 16 is the coordinate to display the text at. 'score: 0' is the default string to display and the object that follows contains a font size and fill color. By not specifying which font we'll actually use the Phaser default, which is Courier.

Next we need to modify the `collectStar` function so that when the player picks-up a star their score increases and the text is updated to reflect this:

```
function collectStar (player, star)
{
    star.disableBody(true, true);

    score += 10;
    scoreText.setText('Score: ' + score);
}
```

So 10 points are added for every star and the `scoreText` is updated to show this new total. If you run `part9.html` you will see the stars fall and the score increase as you collect them.

![image](part9.png)

In the final part we'll add some baddies.