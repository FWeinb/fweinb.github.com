---
layout: post
published: false
title: Direction Aware Hover In Pure CSS
draft: true
---

<pre class="codepen" data-height="300" data-type="result" data-href="162ba1b75de88267c79052fb6c431c70" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/xgCwL">Check out this Pen!</a></pre>

A few days ago I had the idea to implement the direction aware hover effect I saw on [codedrops](http://tympanus.net/TipsTricks/DirectionAwareHoverEffect/) in pure CSS. The main goal was to uses as few elements as possible to not clutter the DOM with none semantic elements. Additionally I want to add different content on each panel. 

## The Basic Structure

The main concept is quite simple. For simplicity I will only explain how to create this effect for the `.box__right` property, the rest should be self explanatory. Let's begin with the bar minimum: 
<pre class="codepen" data-height="300" data-type="css" data-href="882abf79f7211b64071f84614b149c4c" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/hDgKr">Check out this Pen!</a></pre>

The `.box` will hold the elements for each side. The inner `.box__*`'s will be the extract same size as the `.box` itself using CSS inheritance like `width:inherit;` `height:inherit;`.

To better see what is going on, I colored the `.box` in green and `.box__right` in red. You can see the result by switching to the result tab on the embedded pen. You will see a red box with the content "Right → Left" because the `.box__right` is above the `.box` container. 

## Determine The Hover Direction 

This is the most tricky part. But can be solved by using a pseudo element and a little bit of thinking. The first thing to do is to hide the `.box__right` by moving it to the right using `transform:translateX(100%);` these 100 percent referee to the parent element with a `position:relative;`set. In this case to the `.box` element. 
But that is not enough, moving the `.box` 100 percent to the right makes it impossible to hover and therefor impossible to detect the direction of the hover. 

### :Pseudo Elements To The Rescue 

Another great thing about pseudo elements is that they extend the hover-able region of the whole element. Let's add a `:before` pseudo element to the mix. 

<pre class="codepen" data-height="400" data-type="result" data-href="7e9b4dfe299e0ef903ad66f77384fda4" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/iaJLG">Check out this Pen!</a></pre>
<aside>
For this demo I added the ability to toggle the `overflow:hidden` property to better understand what is going on. 
</aside>

Moving the `.box__right` 100 percent to the right made it invisible. Only after adding the yellow colored pseudo element it's possible to hover it again. 

To see how it works disable the `overflow:hidden` and hover the yellow pseudo element. You will see that the real elements background get's blue. 

### Show The Content On Hover

The first thing to do is to add `transition:transform .4s ease` to the `.box__right` to get a nice sliding effect.

The hover effect is splitted into to parts. The first hover effect will move the `.box__right`content in the viewport again and the second will ensure that the pseudo element covers the hole container to make sure you can't lose the over while moving the mouse in another direction. 

<pre class="codepen" data-height="300" data-type="result" data-href="9ddf05a4443a1e66e69cc305e0f75702" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/GnleK">Check out this Pen!</a></pre>


# Final Words

After reading this creating the boxes for the other directions should be straight forward. Only the `.box__center` is special but luckily there is the general sibling combinator selector `~` with it's help modifying the `.box__center` is very simple. Just have a look at the final code [here](http://codepen.io/FWeinb/details/GrpqB). Don't be afraid that the code there is a little different. I used a [placeholder selector](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#placeholder_selectors_) to abstract the common parts from each box. 

Finally I hope you enjoyed reading this and learned some new tricks. Maybe you want to follow me on [Twitter](http://twitter.com/FWeinb). 





<script async src="http://codepen.io/assets/embed/ei.js"></script>
