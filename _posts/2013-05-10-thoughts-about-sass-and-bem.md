---
title: Thoughts About SCSS and BEM
layout: post
published: true
---

Writing efficent CSS is hard, we all know that. There are [many][1] [articles][2] [out][3] [there][4] regarding this topic.
I don't want do repeat everything said in these articels.
Rather I want to share my thoughts about [BEM] in combination with [SCSS].

[1]: http://csswizardry.com/2011/09/writing-efficient-css-selectors/
[2]: http://www.whoishostingthis.com/resources/efficient-css/
[3]: http://css-tricks.com/efficiently-rendering-css/
[4]: https://developers.google.com/speed/docs/best-practices/rendering

## What is BEM?

BEM stands for **B**lock**E**lement**M**odifier and is a naming convention created by [Yandex].
I first heard of it in [Harry Roberts](http://csswizardry.com/) articel [MindBEMding – getting your head ’round BEM syntax] [MindBEMding],
if you haven't heard of it yet you should definitely read that articel first.

[5]: http://nicolasgallagher.com/about-html-semantics-front-end-architecture/
[MindBEMding]: http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/
[SCSS]: http://sass-lang.com/
[BEM]:  http://bem.info/
[Yandex]: http://www.yandex.ru/

## Using BEM in SCSS

I am using SCSS to write my CSS but when it comes to BEM the syntax isn't optimal.
SCSS is great but can be improved reagarding BEM syntax.


### A simple example

This is what a BEM structure would currently look like in SCSS

```css
.block{
}
    .block__element{
    }
    .block--modifier{
    }

```

To be honest, this is just plain CSS no SCSS feature was used. But what is the Problem with that?
There is to much replication. You can see that '.block' is written three times there.

<aside>This is currently not working in SCSS but they are working in that direction. See Issue #[286](https://github.com/nex3/sass/issues/286)</aside>

In SCSS there is the [Referencing Parent Selectors](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#referencing_parent_selectors_): `&` which is most often use in combination with pseudo classes like `:hover`, `:before` or `:after`.

But woudn't it be great to write BEM SCSS like this:

```scss
.block{
    &__element{
    }
    &--modifier{
    }
}
```
to get:

```css
.block{
}
.block__element{
}
.block--modifier{
}
```

The great thing about this would be that elements and modifiert would be block agnostic. So it would be possible to have shared modifiers like this:

```scss
%sharedModifier{
    &--blue{
        color:blue;
    }
    &--green{
        color:green;
    }
}

.block1{
    @extend %sharedModifier;
}

.block2{
    @extend %sharedModifier;
}

```

Resulting in:

```css
.block1{
}
.block2{
}
.block1--blue, .block2--blue{
    color:blue;
}
.block1--green, .block2--green{
    color:green;
}
```

# Wrapping up

It's just a small change to SASS but, in my eyes, it would greatly improve the readability of SCSS.

I would like to know what you think about this syntax. Is it superfluous, or do you think it's usefull? Have you any other idea on how to
improve SCSS?
