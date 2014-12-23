---
layout: post
categories: CSS
title: "Getting started with CSS Structure"
by: "Brad Westfall"
level: "Beginner"
---

Web pages are made out of rectangles or "blocks" as we call them. When we write HTML tags the browser renders each tag into an "element" which is rectangular in shape. Elements should be thought of as containers which hold text and other elements to form a page. The process of converting tags to elements and rendering them into a page is sometimes known as "reflow". You can watch this [reflow visualization](https://www.youtube.com/watch?v=ZTnIxIA5KGw) to get a glimpse of how the process works.

## CSS Display

The cornerstone of CSS structure lies in the a CSS property called `display`. Elements are typically `display: block` or `display: inline` by default. Before we get into lengthy descriptions of these two types of values, let's visualize the difference. The following example shows three elements as `display: block`. Use the buttons to contrast block with inline:

<iframe src="/demo/display/toggle.html" class="x2"></iframe>

Block-level elements stack on top of each other and stretch as wide as their available space. In contrast, Inline-level elements stay on the same line and are only as wide as their content. As previously stated, almost every HTML tag will create an element that either inline or block, but as with the example, elements can be changed away from their defaults.

## Inline Elements

Inline elements are common for short spans of text. Some common tags that are inline by default are:

- `<b>` or `<strong>` for bold text
- `<i>` or `<em>` for emphasized (italic) text
- `<a>` for anchors (links)
- `<u>` for underline text
- `<button>` for buttons, obviously :)
- `<span>` for generic, non-semantic inline text

These inline tags will create elements that will appear "inline" with each other (or "side-by-side") when rendered:

<div class="demo spacing">
	<span class="colorize">Here is our first inline tag.</span><span class="colorize">Here is the second</span><span class="colorize">Third...</span>
</div>
```html
<span>Here is our first inline tag.</span><span>Here is the second</span><span>Third...</span>
```

### Inline Gap

Notice with the previous example that the rendered elements are touching? This is because the HTML was written on one line without [new lines](http://en.wikipedia.org/wiki/Newline). If we change the HTML so each `<span>` tag is written on it's own line, notice it causes a gap between the rendered span tags:

<div class="demo spacing">
	<span class="colorize">Here is our first inline tag.</span>
	<span class="colorize">Here is the second</span>
	<span class="colorize">Third...</span>
</div>
```html
<span>Here is our first inline tag.</span>
<span>Here is the second</span>
<span>Third...</span>
```

This is to be expected; however, did you also notice that the elements are still "inline" with each other when rendered regardless of how the HTML is written? This is a key concept to grasp. HTML is discretionary with regards to our style but has little effect over the rendering of the page - with the one exception being that "inline gap".

Our next example further illustrates this point. We'll use different inline-level tags within the context of a sentence. Again, the HTML is written with each tag on its own line but the elements all stay on the same line when rendered:

<div class="demo">
	<p>
	 	The
		<span class="colorize">quick</span>
		brown
		<strong class="colorize">fox</strong>
		jumps
		<em class="colorize">over the lazy</em>
		dog.
	</p>
</div>
```html
<p>
	The
	<span>quick</span>
	brown
	<strong>fox</strong>
	jumps
	<em>over the lazy</em>
	dog.
</p>
```

## Block Elements

Where inline elements are only as wide as their contents, block elements take up all available horizontal space unless otherwise specified:

<div class="demo">
	<div class="colorize">
		No width specified
	</div>
	<div class="colorize" style="width: 300px">
		width: 300px;
	</div>
	<div class="colorize" style="width: 200px">
		width: 200px;
	</div>
</div>

```html
<div>
	No width specified
</div>
<div style="width: 300px">
	width: 300px;
</div>
<div style="width: 200px">
	width: 200px;
</div>
```

The other defining characteristic of block elements is how they stack. Notice that even when there is enough room for the 300px and 200px elements to share the same line, they don't.
