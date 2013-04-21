---
title: Continously Rotating Element
layout: post
---

Just a quick CSS3 transitions and animations tip today. After cleaning up my dropbox I found some old code of mine implementing a little game in another programming language using OpenGL to draw everything, the code dated back to 2009. I thought I'd rewrite it in JavaScript and render it using CSS/HTML.

<aside>I am using CodePen to embed code so you can always see the result by switching to the Result tab. Prefix free is used so keep in mind to add vendor prefixes in real code.</aside>

The game logic is quite simple, you click on a circle which then rotates 90deg clockwise and if the white pipe get's connected with surrounding ones, these will rotate the same way.

You can try a live demo here:
<pre class="codepen" data-height="740" data-type="result" data-href="JjBhk" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/JjBhk">Check out this Pen!</a></pre>

If you watch these little circles after clicking on one you can see that they rotate continously. These circles have four states;  0, 90, 180 or 270 degrees rotated clockwise. These states are represented by a CSS selector (in this case a attribute selector). Now to create a continous animation between these states always rotating clockwise, I first started using a simple transition like this:

<pre class="codepen" data-height="300" data-type="css" data-href="e41290586d3c2579ef0c90f44fbae956" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/bJCfo">Check out this Pen!</a></pre>


You my notice that everything looks good except the transition between `data-state='3'` and `data-state='0' where the whole circle rotates anti-clockwise.
To figure out why this is happening lets look at the angles that are involved in all these transition:

`0 -> 90 -> 180 -> 270 -> 0`

And there it is! Between the first three transition we are increasing the angle with results in a clockwise rotation. Only in the last transition there is a decreate, and therefor a anti-clockwise rotation.


## How to solve it?

After asking the [#4ae9b8 Team](4ae9b8.com) for help, [Sara Soueidan](http://sarasoueidan.com/) suggest to use CSS animations for it.

So I gave it a try:
<pre class="codepen" data-height="300" data-type="css" data-href="2adb7073fca4e81afe331cce079f2b62" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/vhzyg">Check out this Pen!</a></pre>

Woah, this is quite much code. Four animations are needed for this to work. I first thourght that it would be possible to omit the `0%{}` declaration in `@keyframes` because setting the `animation-fill-mode:forwards` but after the state change the animation isn't applyed to the element anymore.

It's working but is far away from usable, even after jumped in [Hugo Griaudle](http://hugogiraudel.com/) and made a SASS mixin for [it](http://jsfiddle.net/TD8zW/2/) (he just makes a mixing for everything).


## Everything is a Remix!

The first attempt was quite successfull, only the last transition was not working. Let's mix both techniques:
<pre class="codepen" data-height="300" data-type="css" data-href="5d8005ffc8efe242917b7df6ea9de016" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/HnFJd">Check out this Pen!</a></pre>

This looks much better. For the first three state changes CSS transition are used and for the last one a animation from 270 to 360 degree.
So there is only the need of one insted of four animations now. But there is a problem! This only works in WebKit (so Chrome and Safari as of writing).

<aside>I don't know if this is a Bug in Firefox or in Webkit or even an unclearence in the Spec, but I would like to now! So if you have any information about this, please let me know.</aside>

## Wrapping it up

For my little game I am currently using the second solution with only animations because that has better browser support.
Thanks for reading and you have any ideas on how to improve this please let me know!


<script async src="http://codepen.io/assets/embed/ei.js"></script>