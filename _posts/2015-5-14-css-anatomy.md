---
layout: post
title: "CSS Anatomy"
by: "Brad Westfall"
level: 1
categories: [fundamentals, terminology]
permalink: /css-anatomy
---

Terminology is important in all areas of Computer Science and CSS has no shortage of terms. These are the main terms that make up the syntax of CSS.

## Basic Parts

Three must-know terms in CSS are **selector**, **property**, and **value**:

<pre class="breakout css-anatomy">
<span class="selector">header nav a</span> {
    <span class="property">display</span>: <span class="value">inline-block</span>;
    <span class="property">padding</span>: <span class="value">10px 5px</span>;
}
</pre>

<div class="legend">
    <span class="key selector"><span>Selector</span></span>
    <span class="key property"><span>Property</span></span>
    <span class="key value"><span>Value</span></span>
</div>

These terms describe the basic parts of CSS. Selectors describe which [DOM elements](/terminology/tags-vs-elements.html) this set of rules applies to. 

## Target 

<pre class="breakout css-anatomy">
<span class="selector">header nav</span> <span class="target">a</span> {
    display: inline-block;
    padding: 10px 5px;
}
</pre>

<div class="legend">
    <span class="key selector"><span>Context</span></span>
    <span class="key target"><span>Target</span></span>
</div>

The **target** (the element being selected) is the part of the selector on the far right. The rest of the selector is just there for context. In other words, even though this selector has three elements: `header`, `nav`, and `a`, the only thing being selected is `a` because it is the **target**. So this selector finds all `a` (anchors) that are within `nav` elements that are within `header` elements.

<p class="notice">
Note that the term "context" here isn't an official term in CSS. We're just using that word to describe the rest of the CSS selector that isn't the target.
</p>

## Ruleset

And finally, the whole group is called a **ruleset**:

<pre class="breakout css-anatomy">
<span class="ruleset">header nav a {
    display: inline-block;
    padding: 10px 5px;
}</span>
</pre>

<div class="legend">
    <span class="key ruleset"><span>Ruleset</span></span>
</div>