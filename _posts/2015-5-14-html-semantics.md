---
layout: post
title: "HTML Semantics"
by: "Brad Westfall"
level: 1
categories: [fundamentals, terminology]
permalink: /html-semantics
---

<img src="/images/articles/web-design-layout.jpg" alt="Web Design and Layout">

Semantics is the study of meaning. In HTML, semantics describes the meaning of tags. All tags create a rectangle, sometimes referred to as a [box](/css-box-model). From a behavior standpoint, there is little difference between a `<div>` tag and a `<p>` tag. Sure `<p>` tag starts off with margin but that can be overridden in CSS to make it more div-like. Or we could add margin to the `<div>` tag and essentially make `div`'s and `p`'s look the exact same. We could make anchors look like headings and `h1`'s look like `span`'s because of the power of CSS. So then what difference does it make what tags you chose?

The difference is the semantic difference. We could make `div` tags look like `p` tags with CSS if we really wanted to but there are two downsides to doing so:

1. If we just used one tag for all elements or if we misuse tags it makes our HTML less readable.
2. Devices (phones, tablets, etc) and crawlers (like Google's search engine crawler) would have a hard time understanding the meaningfulness of your markup if you used improper tags

## The olden days

Before 2010, the web was largely made up of the HTML 4.01 spec from the [W3C](http://en.wikipedia.org/wiki/World_Wide_Web_Consortium). There were a limited number of "sematic" tags available to us. Most notable were `p` for paragraph, `ul` and `ol` for lists, `b` for bold, `i` for italic, etc...

Some tags were [inline and some were block](/css-display-inline-vs-block/). If one wanted a block-level tag and there were no semantic tags for it, we would use a `div`. If one wanted an inline-level tag and there were no semantic tags for it, we would use `span`. You might say that `div` and `span` were the ["meaningless" or "semantic-less" tags](http://en.wikipedia.org/wiki/Span_and_div).

The problem was there was a need to make the same things over and over but there wasn't a right tool for the job. Take headers for example:

```html
<div class="header"></div>
<div class="primary-header"></div>
<div class="head"></div>
<div class="main-header"></div>
```

Every website has one, but since there were no specific semantic tags for this, we used `div` tags and class names to indicate it was our header. While it did lead to some confusion if a developer used really bad class names, there was nothing technically wrong with it. We used funny terms like "div-itis" or "div-soup" to describe websites that were largely made up of the `div` tag.

As time progressed, devices and crawlers wanted to become more sophisticated and the abundant use of meaningless `div` tags did start to pose a problem. While a person might be able to tell the semantic difference these two:

```html
<div class="header"></div>
<div class="article"></div>
```

It's more difficult for a computer program to tell the difference, not because a computer program can't be programmed to look in the class name, but because 1000s of developers would use too many variations of class names to describe the same thing.

It was time for more semantic tags

## HTML 5 Semantic Tags

HTML 5 brought many changes to web development and some of the first changes to take mainstream were the new semantic tags. If felt awkward at first after years of doing `<div class="header">` and `<div class="footer">`. But finally we got sematic tags!

```html
<header></header>
<footer></footer>
<aside></aside>
<nav></nav>
<main></main>
<article></article>
<section></section>
```

> See a more comprehensive list at [w3schools](http://www.w3schools.com/htmL/html5_semantic_elements.asp)

The problem now was that no browser supported all the semantic tags, plus at the time Internet Explorer 7 and 8 were very popular and had no intentions of ever supporting the new semantic tags.

This sparked development for [shivs and shims](http://www.programmerinterview.com/index.php/html5/what-is-a-shiv-in-html5/) such as [HTML5 Shiv](http://en.wikipedia.org/wiki/HTML5_Shiv) which allowed us to use the modern semantic tags while still working on older browsers. Later the popular [Modernizr](http://en.wikipedia.org/wiki/Modernizr) took the web by storm which provided a shim for semantic tags among other things. Today Modernizr is still a very popular tool to use.

<div class="notice">
    <h3>Do we still need div and span tags?</h3>
    Sure we do. By no means were semantic tags supposed to replace the need for non-semantic tags like `div` and `span`. It's just nice that we don't have to use as many of them.    
</div>

## Semantic `<input>`

In addition to new tags, HTML 5 also brought us new semantic `input` types. Previously we only had a few:

```html
<input type="text">
<input type="checkbox">
<input type="radio">
<input type="button">
<input type="submit">
```

With HTML 5, it was now possible to have

```html
<input type="color">
<input type="date">
<input type="datetime">
<input type="datetime-local">
<input type="email">
<input type="month">
<input type="number">
<input type="range">
<input type="search">
<input type="tel">
<input type="time">
<input type="url">
<input type="week">
```

<div class="footnote">
    List provided by <a href="http://www.w3schools.com/htmL/html_form_input_types.asp">w3schools</a>
</div>

The new types tell devices what type of keyboard to use when the user is typing in a field. A good example would be the `email` type. When the user clicks on this field, devices are supposed to show a button for `@` and `.com` without having to use the shift key. It might seem trivial, but it makes a big user experience difference.

## Content, not Design

In the early 2000s there was a paradigm shift away from doing "design" related things in our HTML and doing "content-only" things instead. For example, it became very unpopular to use the font tag:

```html
<font color="yellow">This is some text!</font>
```

These types of tags describe the look of the element. Instead, web designers started to realize the power of doing all their design in CSS and only using HTML to "describe" the content. Today, one is more likely to do this:

```html
<span class="highlight">This is some text!</span>
```

The span tag can "describe" the content better by using a class name then we can use CSS to take care of what elements with `highlight` look like. This makes our site more maintainable and promotes the computer concept: [Separation of Concerns](http://en.wikipedia.org/wiki/Separation_of_concerns)

Keeping "design" out of HTML also made these tags unpopular:

```html
<br>
<hr>
<b>bold</b>
<u>underline</u>
<i>italic</i>
```

One could use CSS solutions or more semantic tags to replace these old ones. For instance, the `<b>` tag is commonly replaced by the `<strong>` tag and the `<i>` tag is commonly replaced by the `<em>` (emphasis) tag

## Additional Reading

- [Wikipedia: Semantic HTML](http://en.wikipedia.org/wiki/Semantic_HTML)
- [HTML5 Doctor: Let's talk about semantics](http://html5doctor.com/lets-talk-about-semantics/)
- [Semantic Code: What? Why? How?](https://boagworld.com/dev/semantic-code-what-why-how/)