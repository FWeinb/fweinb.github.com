---
published: false
layout: post
title: "About Prose.io and why it's awesome!"

---

Writing a blog post with Jekyll goes like this:

1. Find your Computer
2. Fire up your favorit editor (e.g. Sublime Text 2)
3. Write the blog post
4. Commit


## What is the problem with that?

You have to be on your Computer and have everything setup to commit to your GitHub acccount. You could argue that this is fine in 99% percent of the cases, but in those where you don't have access to your computer you can't fix that annyoing typo someone pointed out to you and you are so deeply ashamed of.

## How to fix it?

Meet [Prose.io](http://prose.io) I just found it 10 Minutes ago and am writing this blog post with it!

![Screenshot of this blog post ](/images/screenshot.png)


## Getting started with Prose.io 

Prose.io is completly open source and build with [Backbone.js](http://backbonejs.org/) you can [host it yourself](https://github.com/prose/prose/blob/master/CONTRIBUTING.md#building--installing) or just sign in with your GitHub account on [Prose.io](http://prose.io)

## Settings up your \_config.yml

This step is optional but will increase the comfort of editing your articles with Prose.io greatly.
I never worked with [YAML](http://www.yaml.org/) before and therefor I was quite irritated about the syntax. Be after reading the [documentation for prose](https://github.com/prose/prose/wiki/Configuration) you are getting used to it.

I ended up with this:
<div class="highlight-full-view">
```yaml
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
</div>



Basicly this tells prose where your blog/site is hosted (`siteurl`) and where to look for media fiels (`media`). 

The `metadata` field is the interesting part here. 



