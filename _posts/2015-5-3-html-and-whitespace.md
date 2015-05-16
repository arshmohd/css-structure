---
layout: post
title: "HTML and Whitespace"
by: "Brad Westfall"
level: 1
categories: [fundamentals, terminology, HTML]
permalink: /html-and-whitespace
---

Whitespace is defined as any character that does not make a visible mark. You can also think of it as any character that when printed, wouldn't use any ink. The most common whitespace characters are spaces, tabs, and [hard-returns](http://www.webopedia.com/TERM/H/hard_return.html). The relationship between HTML and whitespace characters is important in that the browser ignores whitespace characters when rendering the output.

Here's a basic example showing how two words written on two lines (without HTML tags) will result in the output having those two works on one line.

```html
Hello
World
```

<div class="demo">
    Hello
    World
</div>

The browser always reduces all whitespace characters that you type in HTML, to one space. In the example, our hard return was ignored and reduced to a space.

Let's see a different example. This HTML:

```html
Hello
       

       World
```

<div class="demo">
Hello


       World
</div>

In this case, the code has several hard returns and spaces between the two words. Again the browser has reduced all this whitespace down to one space.

So does whitespace matter at all in HTML? The answer is it almost never does. This was done on purpose to give HTML authors freedom to write their HTML with different styles. When writing HTML, it's important to make it look nice so others can read it and understand it. The process of making HTML look nice is called beautification and is accomplished by [nesting our HTML](/html-nesting) in ways that we think looks attractive to read.

If two different HTML authors have different nesting styles, the resulting output should be the same since the tabs and hard returns used in the nesting process will be ignored.

Let's look at three ways of nesting the same anchor inside a paragraph:

```html
<!-- Technique One -->
<p><a href="http://google.com">Google</a></p>

<!-- Technique Two -->
<p>
    <a href="http://google.com">Google</a>
</p>

<!-- Technique Three -->
<p>
    <a href="http://google.com">
        Google
    </a>
</p>
```

Which one is correct? Technically all of them are correct. Choosing how you want to nest your HTML is up to you. There are some common [nesting strategies](/HTML-Nesting) that most developers adhere to, but ultimately the browser doesn't care.

## What does this have to do with CSS?

Normally the way one writes and nests their HTML doesn't matter for the output. But it can matter for [inline elements](/css-display-inline-vs-block). There's one little detail that we need to examine where the whitespace matters. Let's do an example to understand that detail:

```html
<span>One</span>
<span>Two</span>
<span>Three</span>
```

This code will result in:

<div class="demo">
<span class="colorize">One</span>
<span class="colorize">Two</span>
<span class="colorize">Three</span>  
</div>

The detail that's worth knowing about is the gap that appears between the elements. Note that for demo purposes we colorized the backgrounds to illustrate this point to show the gap.

If we want that gap then the way we wrote our HTML works out for us. But what if we don't want that gap? The answer is not to use some hack like margin to close the gap because the gap isn't made with margin in the first place. The gap is made from the fact that the hard returns between each line of HTML will be reduced to a space.

So let's write our HTML without hard returns:

```html
<span>One</span><span>Two</span><span>Three</span>
```

<div class="demo">
<span class="colorize">One</span><span class="colorize">Two</span><span class="colorize">Three</span>  
</div>

Now the space between the buttons goes away. 

This might seem pointless or trivial, but it's these subtle details that become big talking points later on. Keep in mind that this gap happens with [inline elements](/css-display-inline-vs-block) only which means anchors, buttons, input fields and more.

If you're interested in seeing a more advanced article where this gap topic with inline elements really matters, see [display: inline-block](/css-display-inline-block)