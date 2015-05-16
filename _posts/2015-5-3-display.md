---
layout: post
title: "The Display Property"
by: "Brad Westfall"
level: 1
categories: [display, box-model, fundamentals]
permalink: /css-display-inline-vs-block/
---

The `display` property is CSS' most fundamental property for structure. Every element on the page is effected by having this property applied to it. Almost all elements have `display: block` or `display: inline` applied to them by default. The high level differences are as follows:

### Inline Elements

Inline elements have these characteristics by default:

- Take as much width as their content
- Arrange themselves on the same horizontal line (inline)

<div class="demo">
	<span class="colorize">Span (Inline)</span>
	<span class="colorize">Span (Inline)</span>
	<span class="colorize">Span (Inline)</span>
</div>

### Block Elements

Block elements have these characteristics by default:

- Are as wide as they can be with the available space given
- Stack on top of each other

<div class="demo">
	<div class="colorize">Div (Block)</div>
	<div class="colorize">Div (Block)</div>
	<div class="colorize">Div (Block)</div>
</div>

<div class="notice">
	Note that demos on this page will use colorized backgrounds just to illustrate the mechanics of how elements work. 
</div>


## Inline Elements

Inline elements are common for small pieces of text. Here are some common tags that are inline by default:

- `<b>` and `<strong>` for bold text
- `<i>` and `<em>` italic (or emphasized) text
- `<a>` for anchors (links)
- `<u>` for underline text
- `<button>`
- `<span>` for generic, [non-semantic](/html-semantics) inline text

Let's use three span tags to see how they will be rendered as elements:

<div class="demo">
	<span class="colorize">Here is the first inline tag.</span>
	<span class="colorize">Here is the second</span>
	<span class="colorize">Third...</span>
</div>

```html
<span>Here is the first inline element</span>
<span>Here is the second</span>
<span>Third...</span>
```

Notice that they align together horizontally? That's what it means to be "inline". Also notice that each element is only as wide as its contents? Those are the two main characteristics of inline elements.

However, there's a sneaky third characteristic. Did you notice that there's a gap between the elements? This gap happens when we write our HTML on separate lines. Here is the same example but with the `span` tags written all on one line:


<div class="demo spacing">
	<span class="colorize">Here is our first inline tag.</span><span class="colorize">Here is the second</span><span class="colorize">Third...</span>
</div>
```html
<span>Here is our first inline tag.</span><span>Here is the second</span><span>Third...</span>
```

Now the gap closes because the `span` tags are written without [hard-returns](http://www.webopedia.com/TERM/H/hard_return.html). This is an important concept that will come up in future articles. Browsers reduce all [whitespace](/html-and-whitespace) down to a single "space" character. Since hard-returns are considered white space, rendering these three elements will result in the browser putting once space between them. Try to remember this for future articles because it makes a huge difference later on.

There's another key takeaway here. It doesn't matter how we write our HTML when it comes to  block vs inline. Whether we write the three spans one their own line or on the same line, spans are "inline elements" and therefore will be rendered inline with each other.

This next example further illustrates the point on whitespace. We'll use different inline tags within the context of a sentence. Again, the HTML is written with each tag on its own line but the elements all stay on the same line when rendered:

<div class="demo">
 	The
	<span style="width: 200px" class="colorize">quick</span>
	brown
	<strong class="colorize">fox</strong>
	jumps
	<em class="colorize">over the lazy</em>
	dog.
</div>
```html
The
<span>quick</span>
brown
<strong>fox</strong>
jumps
<em>over the lazy</em>
dog.
```

## Block Elements

Block elements are commonly used as containers for other elements. Here are some common tags that are block by default:

- `<p>` for paragraphs
- `<header>`
- `<footer>`
- `<nav>`
- `<div>` for generic, [non-semantic](/html-semantics) block elements

Block elements contrast well with inline elements because they take up all available horizontal space by default instead of being horizontally aligned:

<div class="demo">
	<div class="colorize">Here is the first block element</div>
	<div class="colorize">Here is the second</div>
	<div class="colorize">Third...</div>
</div>

```html
<div>Here is the first block element</div>
<div>Here is the second</div>
<div>Third...</div>
```

Whereas inline elements are only as wide as their content, block elements take up all the available horizontal space by default. 

However, the width of block elements can be adjusted:

<div class="demo">
	<div class="colorize">No width specified</div>
	<div class="colorize" style="width: 200px">width: 300px;</div>
	<div class="colorize" style="width: 100px">width: 200px;</div>
</div>

```html
<div>No width specified</div>
<div style="width: 200px">width: 200px;</div>
<div style="width: 100px">width: 100px;</div>
```

The other defining characteristic of block elements is how they stack on top of each other. Notice that even when there is enough room for the last two elements to share the same line, they don't.

So what will happen if we write the the HTML all on the same line without hard returns?

<div class="demo">
	<div class="colorize">No width specified</div><div class="colorize" style="width: 200px">width: 300px;</div><div class="colorize" style="width: 100px">width: 200px;</div>
</div>
```html
<div>No width specified</div><div style="width: 200px">width: 200px;</div><div style="width: 100px">width: 100px;</div>
```

Nothing happens, that's the whole point! Remember that the block elements are going to be block elements regardless of the whitespace of the HTML.

## Summary

While this isn't the end of the block vs inline story, it's a good point to stop for this article. There are many properties that can be applied to an element that might change the default characteristics of block and inline elements. For beginners however, it's imperative to remember how these two `display` values differ in solitude. 


<div class="related">
<h4>Related Articles:</h4>
	<ul>
	{% for post in site.categories.display %}
	{% if post.title != page.title %}
	<li><a href="{{post.url}}">{{post.title}}</a></li>
	{% endif %}
	{% endfor %}
	</ul>
</div>
