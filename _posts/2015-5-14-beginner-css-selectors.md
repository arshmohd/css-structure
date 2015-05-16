---
layout: post
title: "Beginner CSS Selectors"
by: "Brad Westfall"
level: 1
categories: [fundamentals, selectors]
permalink: /beginner-css-selectors
---

Selectors are the part of CSS that identify what parts of the HTML you want to style. This article is about `tag`, `class`, and `id` selectors.

## Tag Selectors

Let's assume we have this small chunk of HTML and we want to give each piece of text a different color:

```html
<div>Hello</div>
<p>HTML</p>
<span>World</span>
```

Since each piece of text is in a different HTML tag, here's some CSS that would do the job:

```css
div {
    color: blue;
}

p {
    color: green;
}

span {
    color: red;
}
```

<div class="demo">
    <div style="color: blue">Hello</div>
    <p style="color: green">HTML</p>
    <span style="color: red">World</span>
</div>

In the example above, we're using tag-names as selectors. To use tag-name based selectors, the selector must match the tag name exactly. In other words, if the tag we want to select is a `<div>`, then the selector needs to be `div`.

## Class Selectors

Let's make the situation slightly more difficult with this new HTML. 

```html
<div>Dave</div>
<div>Web Designer</div>
```

How would we give each piece of text a different color? Using tag selectors from the previous example wont work because the `div` selector will select all the tags. But let's see what would happen if we tried:

```css
div {
    color: red;
}

div {
    color: blue;
}
```

This CSS will result in both pieces of text being blue. In CSS, it's possible to override previous rules. Since both selectors match the same HTML, the later of the two has the ability to override the first if the same [CSS properties](/css-anatomy) are used.

In order to prevent this, we'll need to isolate them with class names:

```html
<div class="name">Dave</div>
<div class="occupation">Web Designer</div>
```

In the CSS, we can address each element now by it's tag name and class name:

```css
div.name {
    color: red;
}

div.occupation {
    color: blue;
}
```

The end result here will be a red <span style="color: red">Dave</span> and a blue <span style="color: blue">Web Designer</span> text.

### Omit Tag Names

With the previous CSS example, it is possible (and often times encouraged) to omit the tag names:

```css
.name {
    color: red;
}

.occupation {
    color: blue;
}
```

Keep in mind that the `.` dot in a CSS selector always means we're using a class name. When we omit the tag-name from the selector we still use a dot to indicate the class name.

In more advanced articles about [CSS Specificity](/css-specificity), we'll dive into why you might want to include the tag name, but for now let's just leave it out.

### Class Reuse

One important detail about class names is that you can use them more than once:

```html
<div class="user">Nicole</div>
<div class="user">Paul</div>
<div class="user">Chris</div>
```

```css
.user {
    background-color: gray;
    color: blue;
}
```

We can select all three `user` elements with one CSS selector. 

But instead of using a class, we could have used a `div` selector like this instead of class names right?

```css
div {
    background-color: gray;
    color: blue;
}
```

Using a `div` tag-name selector would have worked with the current HTML, but this brings us to a new topic of [Defensive CSS](/defensive-css).

Sure the `div` selector could have worked before, but consider that in the future we might add more HTML:

```html
<section>
    <div class="user">Nicole</div>
    <div class="user">Paul</div>
    <div class="user">Chris</div>
</section>

<section>
    <div class="products">Book</div>
    <div class="products">Pen</div>
    <div class="products">Desk</div>
</section>
```

Assuming we want to stylize all users differently from all products, it quickly becomes more obvious that using class selectors has more advantages over tag-name selectors.

## ID Selectors

Similar to classes, IDs are attributes that we can add to HTML tags:

```html
<div id="primary-nav">Primary Nav</div>
```

Stylizing an element with an ID works similarly to classes, except we use a `#` pound sign instead of dots.

```css
div#primary-nav {
    color: red;
}
```

Just as with class selectors, the tag name can be omitted:

```css
#primary-nav {
    color: red;
}
```

## Classes vs IDs

One major difference between classes and IDs is frequency that they can be used. A single class name can be used as many times as you see fit in your HTML. A single ID however is only supposed to exist once within a given page of HTML. Also, it turns out that for more advanced [specificity](/css-specificity) reasons, the use of ID's is sometimes discouraged for CSS selectors. So for most examples we'll use class names instead.

<footer class="pagination">
    <a class="next" href="/css-descendant-selectors">Descendant Selectors</a>
</footer>