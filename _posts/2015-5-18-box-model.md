---
layout: post
title: "CSS Box Model"
by: "Brad Westfall"
level: 2
caegories: [display, box-model, fundamentals, border, padding, margin]
permalink: /css-box-model
---

Many articles have been written on the box-model already. This article will focus on some next-level information you'll need to be aware regarding the effects of the box model on your design.

But first you'll need to understand box-model basics. We suggest these articles:

- [Mozilla Developer Network: Box Model](https://developer.mozilla.org/en-US/docs/Web/CSS/box_model)
- [CSS Tricks: The CSS Box Model](https://css-tricks.com/the-css-box-model/)

## Fundamentals

As a quick review, the box model has three layers which from the inside-out are:

- Content
- Padding
- Border
- Margin

Every element creates a box model. Let's imagine a `span` tag with the text "Hello World". Then let's add some CSS to our `span` tag to see the layers:

```css
span {
    padding: 5px;
    border: 1px solid black;
}
``` 

<img class="bannar" src="/images/articles/box-model-layers.svg" alt="Box Model Layers">

This diagram shows each layer being applied to our `span`. The dotted line illustrates where the content layer is for visual effect. As you can see, the overall horizontal space the element occupies is a combination of the layers. The same concept applied vertically as well.

## By Default

When CSS `width` or `height` is applied to an element, it's the content layer that it's applied to. This single fact has frustrated many developers for years. For many, our intuition tells us that when we state an element is 100px wide, it should be 100px wide.

<img class="bannar" src="/images/articles/box-model-default-width.svg" alt="Box Model Default Width">

However, if so much as 1px of `padding`, `border`, or `margin` is involved, then the overall width of our elements is not our expected 100px.

## Box-Sizing

CSS3 solved our frustrations by introducing [box-sizing](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) - a new CSS property that allows us to state which layer the `width` and `height` should apply to by default.

Without `box-sizing`, let's consider the following CSS:

```css
div {
    width: 100px;
    padding: 10px;
    border: 5px solid red;
}
```

The overall width of this `div` would be 130px wide. This is 100px of width plus 10px of padding (left and right) plus 5px of border (left and right)

Introduce `box-sizing` and now the overall width is 100px wide:

```css
div {
    width: 100px;
    padding: 10px;
    border: 5px solid red;
    box-sizing: border-box;
}
```

Saying `box-sizing: border-box` means we want the width property to apply to the outside of the border layer - effectively the padding and content layer get smashed to fit inside 100px.

See a live example:

<p data-height="302" data-theme-id="0" data-slug-hash="aOZqxP" data-default-tab="result" data-user="bradwestfall" class='codepen'>See the Pen <a href='http://codepen.io/bradwestfall/pen/aOZqxP/'>aOZqxP</a> by Brad Westfall (<a href='http://codepen.io/bradwestfall'>@bradwestfall</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

Play with the HTML, CSS and Result tabs in the live example to see how `box-sizing` is effecting the element's width.

## Conclusion

Understanding the box-model and it's quirks is fundamental to nearly everything you do in CSS. Always keep in the back of your mind the layers of the box model and the rules of where the `width` and `height` with and without `box-sizing`. Here's a video that will further help you understand these concepts:

<iframe width="560" height="315" src="https://www.youtube.com/embed/8KtoC9MpoZ0" frameborder="0" allowfullscreen></iframe>