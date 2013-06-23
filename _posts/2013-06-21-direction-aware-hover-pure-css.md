---
layout: post
published: false
title: Direction Aware Hover In Pure CSS
draft: true
---

<pre class="codepen" data-height="300" data-type="result" data-href="162ba1b75de88267c79052fb6c431c70" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/xgCwL">Check out this Pen!</a></pre>

A few days ago I had the idea to implement the direction aware hover effect I saw on [codedrops](http://tympanus.net/TipsTricks/DirectionAwareHoverEffect/) in pure CSS. The main goal was to uses as few elements as possible to not clutter the DOM with unsemantic elements. Additionaly I want to add diffrent content on each panel. 

## The Basic Structure

The main concept is quite simple. For simplicity I will only explain how to create this effect for the `.box__right` property, the rest should be self explanatory. Let's begin with the bar minimum: 
<pre class="codepen" data-height="300" data-type="css" data-href="882abf79f7211b64071f84614b149c4c" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/hDgKr">Check out this Pen!</a></pre>

The `.box` will hold the elements for each side. The inner `.box__*`'s will be the extact same size as the `.box` itself using CSS inheritance like `width:inherit;` `height:inherit;`.

To better see what is going on, I colored the `.box` in green and `.box__right` in red. You can see the result by switching to the result tab on the embedded pen. You will see a red box with the content "Right → Left" because the `.box__right` is above the `.box` container. 

## Determen The Hover Direction 

This is the most tricky part. But can be solved by using a pseudo element and a little bit of thinking. The first thing to do is to hide the `.box__right` by moving it to the right using `transform:translateX(100%);` these 100 percent refere to the parent element with a `position:relative;`set. In this case to the `.box` element. 
But that is not enough, moving the `.box` 100 percent ot the right makes it impossible to hover and therefor impossible to detect the direction of the hover. 

### :Pseudo Elements To The Rescue 

Another great thing about pseudo elements is that they extend the "hoverable" region of the whole element. Let's add a `:before` pseudo element to the mix. 

<pre class="codepen" data-height="400" data-type="result" data-href="7e9b4dfe299e0ef903ad66f77384fda4" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/iaJLG">Check out this Pen!</a></pre>
<aside>
For this demo I added the abbility to toggel the `overflow:hidden` property to better understand what is going on. 
</aside>

Moving the `.box__right` 100 percent to the right made it invisibel. Only after adding the yellow colored pseudo element it's possible to hover it again. 


### Hovering










<script async src="http://codepen.io/assets/embed/ei.js"></script>
