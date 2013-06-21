---
layout: post
published: false
title: Direction Aware Hover In Pure CSS
draft: true
---



<pre class="codepen" data-height="400" data-type="css" data-href="882abf79f7211b64071f84614b149c4c" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/hDgKr">Check out this Pen!</a></pre>
<script async src="http://codepen.io/assets/embed/ei.js"></script>

A few days ago I had the idea to implement the direction aware hover effect I saw on [codedrops](http://tympanus.net/TipsTricks/DirectionAwareHoverEffect/) in pure CSS. The main goal was to uses as few elements as possible to not clutter the DOM with unsemantic elements. And I want to be to add different content to each panel. 

## The Basic Structure

The main concept is quite simple. For simplicity I will only explain how to create this effect for the `.box__right` property, the rest should be self explanatory. Let's begin with the bar minimum: 
<pre class="codepen" data-height="300" data-type="css" data-href="882abf79f7211b64071f84614b149c4c" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/hDgKr">Check out this Pen!</a></pre

The `.box` will hold the elements for each side. The inner `.box__*`'s will be the extact same size as the `.box` itself using CSS inheritance like `width:inherit;` `height:inherit;`.

To better see what is going on, I colored the `.box` in green and `.box__righ` in red. You can see the result by switching to the result tab on the embedded pen.

## Determen The Hover Direction 

This is the most tricky part. But can be solved by using a pseudo element. Additionaly the content must be moved outsite the viewport to hide it. 

<pre class="codepen" data-height="400" data-type="css" data-href="7e9b4dfe299e0ef903ad66f77384fda4" data-user="FWeinb" data-safe="true"><code></code><a href="http://codepen.io/FWeinb/pen/iaJLG">Check out this Pen!</a></pre>






<script async src="http://codepen.io/assets/embed/ei.js"></script>
