---
published: 
  - "true"
  - published
layout: post
title: "About Prose.io And Why It's Awesome!"

---

Writing a blog post with Jekyll goes like this:

1. Find your Computer
2. Fire up your favorite editor (e.g. Sublime Text 2)
3. Write the blog post
4. Commit


## What is the problem with that?

You must have access to your computer and have everything setup to commit to your GitHub account. You could argue that this is fine in 99% of the cases, but in those where you don't you can't fix that annoying typo someone pointed out to you and you are so deeply ashamed of.

## How to fix it?

Meet [Prose.io](http://prose.io). I just found it yesterday and am writing this blog post with it!

![Screenshot of first blog post with Prose.io](/images/First%20blog%20post.png)

## Getting started with Prose.io 

Prose.io is completely open source and built with [Backbone.js](http://backbonejs.org/). You can [host it yourself](https://github.com/prose/prose/blob/master/CONTRIBUTING.md#building--installing) or just sign in with your GitHub account on [Prose.io](http://prose.io).

## Settings up your \_config.yml

This step is optional but will increase the comfort of editing your articles with Prose.io greatly.
I never worked with [YAML](http://www.yaml.org/) before and therefore was quite irritated about the syntax, but after reading the [documentation for prose](https://github.com/prose/prose/wiki/Configuration) I found myself getting used to it quite fast.

I ended up with this:

```
prose:
  siteurl: "http://blog.weinberg.me"
  media: "images"
  metadata:
    _posts:
      - name: "published"
        field:
          label: "Published"
          element: "checkbox"
          value: "true"
      - name: "layout"
        field:
          label: "Layout"
          element: "text"
          value: "post"
      - name: "title"
        field:
          label: "Title"
          element: "text"
          value: "A awesome Headline!"
```


Basically this tells prose where your blog/site is hosted (`siteurl`) and where to look for media files (`media`). 

The `metadata` field is the most interesting part here. With that field you can customize the Metadata Viewer on Prose.io. Mine looks like this:

![Screenshot of my Metadata Viewer on Prose.io](/images/Metadata%20prose.io.png)

## I really like it!

I am really pleased with what prose.io is offering me. The UI is just beautiful and gets out of the way in most cases. Some would argue that the contrast isn't that good but I like it that way. 
Prose.io isn't limited to be used for your blog. You get access to all your repositories and can edit any file you want; which is great for making quick fixes to your README.md on the go. 

Prose.io closes the last feature that Jekyll on GitHub Pages is missing. You can now edit your articles from the browser without needing access to your computer. 

So check it out and tell me how you like it!
