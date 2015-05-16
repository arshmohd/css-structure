---
layout: post
title: "Descendant Selectors"
by: "Brad Westfall"
level: 1
categories: [fundamentals, terminology]
permalink: /css-descendant-selectors
---

In our [previous article](/beginner-css-selectors) we learned that there can be some strategy when it comes to writing our CSS selectors. We learned that using class selectors can be better than tag-name selectors. However it would be a mistake to think that every element on the page should have class names and that we should avoid tag-name selectors altogether.

Descendant selectors describe elements we want to style by their position or "context" to other elements. Consider this CSS:

```css
a {
    ...
}

div a {
    ...
}
```

The first selector stylizes all anchors, but the second selector uses a space between the `div` and the `a` which means it stylizes all the anchors that are within `div`'s

The space is called a "descendant combinator" and it's important to know that we're not stylizing `div` tags at all. The use of `div` in the selector is there for context.

As we start writing more complex selectors, they will become longer. The actual element we're trying to select is always on the far right of the selector. This is called the **target**. In the previous CSS example, `a` was the target of both selectors.

Assuming the previous CSS example, what would the selector `div a` stylize in this HTML?

```html
<div>
    <a href="#">First</a>
</div>

<p>
    <a href="#">Second</a>
</p>

<a href="#">Third</a>
```

`div a` would only select the "First" anchor because it's the only one inside a `div`.

Let's look at a more realistic example:

```html
<header>
    <a href="/">Company Logo</a>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
        <a href="/contact">Contact</a>
    </nav>
</header>
<main>
    <h1>Welcome to our page</h1>
    <p>We really hope you enjoy the content...</p>
    <a href="/next">Click here for the next article</a>
</main>
```

The two main sections here are `header` and `main`. Let's stylize all the navigation anchors of the header:

```css
header a {
    ...
}
```

This would work right? In a way yes, but it's not ideal. Technically the selector stylizes all four anchors that are in the `header`: the logo and the three inside the `nav`. Since we only want to stylize the ones in the `nav`, we'll need to change our CSS to this:

```css
nav a {
    ...
}
```

There that works! Now we've isolated exactly what we want to stylize without accidentally stylizing anything else. But consider the concept of **Defensive CSS**. Can you think of any problems?

What if we added another `nav` tag later on. For instance, we might want to add a footer which looks like this:

```html
<footer>
    <nav>
        <a href="/privacy">Privacy Policy</a>
    </nav>
</footer>
```

Now the selector `nav a` will stylize anchors in the `header` and in the `footer`. That might not be desirable. To avoid this, there are two common approaches:

One: We can rewrite our selector like this:

```css
header nav a {
    ...
}
```

Or Two: We could add a class name somewhere like this:

```css
.primary-nav a {
    ...
}
```

The second way assumes we rewrote the HTML to look like this:

```html
...
<nav class="primary-nav">
    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="/contact">Contact</a>
</nav>
...
```

Which way is correct? Technically they both work. In more [advanced articles](/defensive-css) we'll talk about why one way is better. But for now it's important to know that they both technically solve our problem.

<footer class="pagination">
    <a class="next" href="/beginner-css-selectors">Beginner Selectors</a>
    <a class="next" href="/css-child-selectors">Child Selectors</a>
</footer>