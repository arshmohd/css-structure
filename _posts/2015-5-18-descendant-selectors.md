---
layout: post
title: "Descendant Selectors"
by: "Brad Westfall"
level: 1
categories: [fundamentals, terminology]
permalink: /css-descendant-selectors
---

In our [previous article](/beginner-css-selectors) we discussed that there can be some strategy when it comes to writing our CSS selectors. We learned that using class selectors can be better than tag-name selectors. However, it would be a mistake to think that every element on the page should have class names and that we should avoid tag-name selectors altogether.

Since tag selectors select too much, and we're not going to give every element a unique class name, we'll need a new type of selector to select elements based on their location (or context).

This leads us into descendant selectors. Consider this CSS:

```css
a {
    ...
}

div a {
    ...
}
```

The first selector stylizes all anchors, whereas the second selector uses a space between the `div` and the `a` which means it stylizes all the anchors that are within `div`'s (descendants of `div`'s)

The space is called a "descendant combinator" and it's important to know that we're not stylizing any `div` elements. The use of `div` in the selector is there for context to say that anchors must reside in `div`'s.

As you start writing more complex selectors, they will become longer. You'll need to consider what the "target" of the selector is - the actual element being styled. On all CSS selectors, the target is the element on the far right-hand side of the selector. In the previous CSS example, `a` was the target of both selectors.

Assuming the previous CSS, `div a` would stylize only one of these anchors:

```html
<div>
    <a href="#">First</a>
</div>

<p>
    <a href="#">Second</a>
</p>

<a href="#">Third</a>
```

It would only stylize the "First" anchor because it's the only one inside a `div`.

Let's look at a more realistic HTML example with a `header` and `main` section:

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

If we wanted to stylize all the anchors of the header navigation, could we do this?

```css
header a {
    ...
}
```

In a way yes, but it's not ideal. Technically the selector stylizes all four anchors that are in the `header`: the logo and the three inside the `nav`. But if we only want to stylize the ones in the `nav`, we'll need to change our CSS to this:

```css
nav a {
    ...
}
```

Now we've isolated exactly what we want to stylize without accidentally stylizing anything else.

While `nav a` works, it isn't exactly **Defensive CSS**. This is because we might need to add more `nav`'s later with anchors and now our selector will stylize those ones too. This would lead to rounds of refacorization in our CSS.

Let's add that additional `nav` tag now to see an example of the problem we created for ourselves. We might want to add a footer which looks like this:

```html
<footer>
    <nav>
        <a href="/privacy">Privacy Policy</a>
    </nav>
</footer>
```

Now the selector `nav a` will stylize the original header's `nav` plus our footer's `nav`. This might not be desirable. It could have been avoided though with are two common approaches:

One: For stylizing the header's `nav`, we can rewrite our selector like this:

```css
header nav a {
    ...
}
```

Two: We could give the `nav` in the header a class name and write out selector like this:

```css
.primary-nav a {
    ...
}
```

With the second approach, we would need to write our HTML this way (with "primary-nav" as a class name)

```html
...
<nav class="primary-nav">
    <a href="/">Home</a>
    <a href="/about">About</a>
    <a href="/contact">Contact</a>
</nav>
...
```

Which way is correct? Technically they both work. In more [advanced articles](/defensive-css) we'll talk about why one way might be considered better. But for now it's important to know that they both technically solve our problem.





<footer class="pagination">
    <a class="next" href="/beginner-css-selectors">Beginner Selectors</a>
    <a class="next" href="/css-child-selectors">Child Selectors</a>
</footer>