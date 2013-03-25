---
title : Style Preview
layout: post
published : false
---

# Codebox

{% highlight scss %}
@mixin pull-quote($direction) {
  $opposite: opposite-position($direction);

  text-align: $opposite;
  float: $direction;
  margin: 0 0 .5em 0;
  margin-#{$opposite}: 1em;
  border-#{$opposite}: 6px solid hotpink;
  padding-#{$opposite}: 1em;
}
{% endhighlight %}

# Codebox full width
<div class="highlight-full-view">
{% highlight scss %}
@mixin pull-quote($direction) {
  $opposite: opposite-position($direction);

  text-align: $opposite;
  float: $direction;
  margin: 0 0 .5em 0;
  margin-#{$opposite}: 1em;
  border-#{$opposite}: 6px solid hotpink;
  padding-#{$opposite}: 1em;
}
{% endhighlight %}
</div>

Lorem ipsum dolor sit amet, consectetur adipisicing elit. Laborum minus nesciunt perspiciatis officiis numquam obcaecati quam deserunt magni eius! Cum ipsa iusto reprehenderit dolores   quas aperiam quod recusandae incidunt eveniet.

# Unorder List
  * Lorem
  * Ipsum
  * Dolor

# Orderd List

  1. Lorem
  1. Ipsum
  1. Dolor


# Block quote
  > Block quote
  > multi
  > row

# Block quote full width

<blockquote class="full-width">
  Block quote full width
</blockquote>


# Aside

<aside>
  Just a aside
</aside>

# Aside full-width

<aside class="full-width">
  Just a full-width aside
</aside>

# Images

## Image left & right
<img src="/images/blog-creating/first-drawing.jpg" class="image-left-block" />
<img src="/images/blog-creating/first-drawing.jpg" class="image-right-block" />
Content will be belowe this images

<img src="/images/blog-creating/first-drawing.jpg" class="image-center" />
Content will be here.

<img src="/images/blog-creating/first-drawing.jpg" class="image-left" />

This content will float around the image
as long as there is space.

