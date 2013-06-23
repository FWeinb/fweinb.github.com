---
layout: post
published: 
  - true
  - published
  - "true"
title: Direction Aware Hover In Pure CSS
draft: true
---

<pre class="codepen" data-height="400" data-type="result" data-href="162ba1b75de88267c79052fb6c431c70" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/xgCwL">Check out this Pen!</a></pre>

A few days ago I had the idea to implement the direction aware hover effect I saw on [Codrops](http://tympanus.net/TipsTricks/DirectionAwareHoverEffect/) in pure CSS. The main goal was to use as few elements as possible to not clutter the DOM with non-semantic elements. Additionally I want to add different content on each panel.

## The Basic Structure

The main concept is quite simple. For simplicity I will only explain how to create this effect for the `.box__right` property, the rest should be self explanatory. Let's begin with the bare minimum:
<pre class="codepen" data-height="400" data-type="css" data-href="882abf79f7211b64071f84614b149c4c" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/hDgKr">Check out this Pen!</a></pre>

The `.box` will hold the elements for each side. The inner `.box__*`'s will be the extract same size as the `.box` itself using CSS inheritance like `width:inherit;` `height:inherit;`.

To better see what is going on, I colored the `.box` in green and `.box__right` in red. You can see the result by switching to the result tab on the embedded pen. You will see a red box with the content "Right → Left" because the `.box__right` is above the `.box` container.

## Determine The Hover Direction

This is the most tricky part, but can be solved by using a pseudo element and a little bit of thinking. The first thing to do is to hide the `.box__right` by moving it to the right using `transform:translateX(100%);` these 100 percent refer to the parent element with a `position:relative;`set. In this case to the `.box` element.
But that is not enough, moving the `.box` 100 percent to the right makes it impossible to hover and therefore impossible to detect the direction of the hover.

### :Pseudo Elements To The Rescue

Another great thing about pseudo elements is that they extend the hover-able region of the whole element. Let's add a `:before` pseudo element to the mix.

<pre class="codepen" data-height="400" data-type="result" data-href="7e9b4dfe299e0ef903ad66f77384fda4" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/iaJLG">Check out this Pen!</a></pre>
<aside>
For this demo I added the ability to toggle the `overflow:hidden` property to better understand what is going on.
</aside>

Moving the `.box__right` 100 percent to the right made it invisible. Only after adding the yellow colored pseudo element it's possible to hover it again.

To see how it works disable the `overflow:hidden` and hover the yellow pseudo element. You will see that the real elements background get's blue.

### Show The Content On Hover

<pre class="codepen" data-height="400" data-type="result" data-href="9ddf05a4443a1e66e69cc305e0f75702" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/GnleK">Check out this Pen!</a></pre>

The first thing to do is to add `transition:transform .4s ease` to the `.box__right` to get a nice sliding effect.

The hover effect is split into two parts. The first hover effect will move the `.box__right` content in the viewport again. Another important thing is to add `z-index:1;` on hover to ensure the other boxes aren't interfering. 
The second hover effect will ensure that the pseudo element covers the whole container to make sure you won't lose the hover while moving the mouse in another direction.

In the sample above You can see both of these hover effects. The pseudo element is yellow and the element will slide in from the right. 

## Lets recap 

After reading this far creating the boxes for the other directions should be straight forward. Only the `.box__center` is special but luckily there is the general sibling combinator selector, `~` with its help modifying the `.box__center` is very simple.

### Adding the .box__center

<aside>
In the demos above I used simplified code. For the following example I will use my final code. Don't be afraid that the code there is a little different. I used a [placeholder selector](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#placeholder_selectors_) to abstract the common parts from each box.
</aside>

<pre class="codepen" data-height="400" data-type="css" data-href="c93eadeb4c412e5fa79f43f64b4203da" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/vpDJa">Check out this Pen!</a></pre>

Starting with the `.box__center` the first thing to do is to ensure that it's not blocking the hover interactions of the other boxes. Because it's the last element in the `.box` it will be initially positioned on top of all the others

The `.box__center` will move on every hover in the same direction as the box that is revealed. There is the need for a third rule on hover, this time modifying the `.box__center`. Adding this for the `.box__right` would involve a selector like `.box__right:hover ~ .box__center` and moving it to the same direction would result in `transform:translateX(100%)`. 

Adding this hover effect for `.box__center` to all boxes and accordingly changing the transformation to the right direction will result in the final code you can see above by switching to the result tab. 


# Final words 

Finally I hope you enjoyed reading this and learned some new tricks. Maybe you want to follow me on [Twitter](http://twitter.com/FWeinb).





<script async src="http://codepen.io/assets/embed/ei.js"></script>
