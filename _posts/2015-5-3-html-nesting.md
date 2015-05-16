---
layout: post
title: "HTML Nesting"
by: "Brad Westfall"
level: 1
categories: [fundamentals, HTML]
permalink: /html-nesting
---

<img src="/images/articles/nesting.jpg" alt="Nesting Dolls">

Many decisions we make in Web Development revolve around maintenance. It's one thing to know where your mind was at yesterday when you wrote some HTML, it's another to see your HTML a year later and remembering what you were thinking. For the purposes of maintenance and readability, you'll want to "beautify" your HTML. To accomplish this, you'll want to "nest" and indent your HTML correctly to make it beautify and easy to read.

Let's start off with an example of un-beautiful HTML:

```html
<header class="primary-header"><a href="#" class="logo">Company Name</a><nav class="primary-nav"><a href="/">Home</a><a href="/about">About</a><a href="/faq">FAQ</a></nav></header>
```

Obviously we would never write our HTML on one line like this. Even though the it will render correctly because the browser doesn't care about how it looks, it's almost impossible to tell what's going on from a readability standpoint. So let's use hard returns to make it a little better:


```html
<header class="primary-header">
<a href="#" class="logo">Company Name</a>
<nav class="primary-nav">
<a href="/">Home</a>
<a href="/about">About</a>
<a href="/faq">FAQ</a>
</nav>
</header>
```

This is better than before, but it's still hard to tell what tags are inside other tags. So now let's use some tabs to make it even more beautiful:

```html
<header class="primary-header">
    <a href="#" class="logo">Company Name</a>
    <nav class="primary-nav">
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/faq">FAQ</a>
    </nav>
</header>
```

Now it's much easier to see what's going on. We can easily see that there is a `header` tag that is the parent tag of the logo anchor and the `nav`. That wasn't so easy to see before the tabs. We can tell this because these two tags are tabbed one level to the right of `header`

Can you see any other parent / child relationships in the previous example? How about the `nav` and it's three child anchors. The `nav` serves as a parent tag to the three anchors even though it also serves as a child tag to the `header`.

It's important to know that it's not the tabbing itself that determines the parent / child relationship. It's where each tag opens and closes. The `nav` tag opens, then hold three anchors, then it closes. It's essentially "wrapped" around the three anchors. That is what makes it a parent - being the tag that wraps around other tags.

<p class="notice">
    Another term we use to describe a tag that wraps around other tags is "container". The difference between the terms "parent" and "container" is that parents are only parents to their direct children. In our example, the <code>header</code> is the parent of the logo and the <code>nav</code>, whereas it is the container of all the tags.
</p>

Let's look at the same example again but with poor tabbing:

```html
<header class="primary-header">
    <a href="#" class="logo">Company Name</a>
    <nav class="primary-nav">
    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="/faq">FAQ</a>
    </nav>
</header>
```

Is the `nav` tag still the parent of the three anchors? The tabbing has been taken away so it's harder to tell right? In this case it is still the parent because it's opening and closing tags still wrap around the anchors. It's more difficult to tell because we didn't tab the three anchors past their parent. This is the virtue of tabbing and beautifying your HTML. The two rules for indentation and nesting are simple to remember:

1. All direct children of a parent are to be tabbed one level past the parent
2. All sibling elements are tabbed to the same level

That second rule we haven't examined yet. Let's take a closer look with our beautiful HTML:

```html
<header class="primary-header">
    <a href="#" class="logo">Company Name</a>
    <nav class="primary-nav">
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/faq">FAQ</a>
    </nav>
</header>
```

In this HTML, the logo anchor and the `nav` are direct children of `header` which makes them siblings. Siblings are always tabbed to the same level - which is what we see here. The three children of the `nav` are all the other anchors. They are siblings with each other so they are also tabbed to the same level.

A common beginner mistake might be to write it this way:

```html
<header class="primary-header">
    <a href="#" class="logo">Company Name</a>
    <nav class="primary-nav">
        <a href="/">Home</a>
            <a href="/about">About</a>
                <a href="/faq">FAQ</a>
    </nav>
</header>
```

When the three sibling anchors are not tabbed at the same level it causes confusion. The confusion comes from our first rule: "All direct children of a parent are to be tabbed one level past the parent". Since the "About" anchor is tabbed one space past the "Home" anchor, it might look like the "Home" anchor is a parent to the "About" anchor which isn't the case.

Another common beginner mistake is this:

```html
<header class="primary-header">
    <a href="#" class="logo">Company Name</a>
    <nav class="primary-nav">
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/faq">FAQ</a>
        </nav>
</header>
```

Can you see the problem? The closing `</nav>` tag looks like it's a sibling to the anchors because they're at the same tab level.

Having one mishap such as this usually leads to more mishaps and very messy HTML. Let's add a `form` to be siblings with `nav`:

```html
<header class="primary-header">
    <a href="#" class="logo">Company Name</a>
    <nav class="primary-nav">
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/faq">FAQ</a>
        </nav>
        <form class="search-form">
            <input type="search">
        </form>
</header>
```

The above HTML is not tabbed well. It looks like we used the closing `</nav>` as a queue to know where to start the form. Even though the page will render just fine because ultimately the way we tab has no impact on rendering, it is hard to tell what tags are containers to what tags. Technically, the form is a sibling to the logo anchor and the `nav` so it should be tabbed in at the same level.

This is better:

```html
<header class="primary-header">
    <a href="#" class="logo">Company Name</a>
    <nav class="primary-nav">
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/faq">FAQ</a>
    </nav>
    <form class="search-form">
        <input type="search">
    </form>
</header>
```

Now it's much easier to see that the `form` is a sibling to the logo anchor and navigation.

## Conclusion

Just remember that it's not the tabbing levels that determines the parent / child relationship - it's the actual nesting. The nesting can be tabbed correctly to look beautiful, or it can have mistakes and look confusing. Almost all the HTML examples shown on this page were the exact same HTML - just with different tabs. All the HTML was valid and would have rendered the same way. So beautification has no impact on how things render and how the technology works, it's merely a way for us to write HTML so that we understand it.