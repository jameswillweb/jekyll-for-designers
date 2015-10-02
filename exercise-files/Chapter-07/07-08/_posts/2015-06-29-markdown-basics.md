---
layout: post
title:  "Markdown Basics"
date:   2015-06-29
tags: [jekyll, markdown, html]
---

In Jekyll, content for pages and posts can be written in either HTML or Markdown. Although there will be times that HTML is the more appropriate choice, Markdown provides a more natural writing environment that makes blogging easier and less of a chore. In this post we’ll examine how Jekyll uses Markdown and cover some basic Markdown syntax.

If you’ve never used it before, Markdown is a text-to-HTML converter that let’s you write text naturally in plain text format and then convert it to valid HTML. To learn more about it, read John Gruber’s post introducing Markdown on [Daring Fireball](http://daringfireball.net/projects/markdown/ "Introducing Markdown").

Jekyll supports multiple Markdown rendering engines and allows you to specify which engine to use in the site’s configuration. Currently Jekyll supports [Kramdown](http://kramdown.gettalong.org/index.html "Kramdown"), [Redcarpet](https://github.com/vmg/redcarpet "Redcarpet"), and [RDiscount](http://dafoster.net/projects/rdiscount/ "Rdiscount"), although you’re free to use any rendering engine you have installed or even write your own! 

To specify a rendering engine, simply add this line to your **_config,yml** file:

~~~~~~~
markdown: kramdown
~~~~~~~

For the most part, the rendering engines are the same, although they do have subtle differences in syntax and element support. Currently Kramdown is the default Markdown renderer for Jekyll. Let’s take a look at some basic Kramdown syntax.

The following passage:

~~~~~~
#My main heading
{: .intro }

This is my initial paragraph. In it I’d like to provide a link to the [Jekyll homepage](http://jekyllrb.com/ "Jekyll"). I want to add **bold** and *italic* formatting to text as well using the `strong` and `emphasis` tags.

This is another paragraph. I’d like to follow it with an unordered list.

* item 1
* item 2
* item 3

~~~~~~

Would be rendered in HTML as:

{% highlight html %}
<h1 class="intro">My main heading</h1>
    <p>This is my initial paragraph. In it I’d like to provide a link to the <a href="http://jekyllrb.com/" title="Jekyll">Jekyll homepage</a>. I want to add <strong>bold</strong> and <em>italic</em> formatting to text as well using the <code>strong</code> and <code>emphasis</code> tags.</p>
	<p>This is another paragraph. I’d like to follow it with an unordered list.</p>
    <ul>
        <li>item 1</li>
        <li>item 2</li>
        <li>item 3</li>
    </ul>
{% endhighlight %}

As you can see, Markdown frees you from many of the structural restraints that would make it difficult to author something like a blog post using HTML. To write two paragraphs, for example, you simply write two paragraphs, no <p> tags or special formatting required. Let’s take a quick look at how to format some of the basic HTML elements in Kramdown.

###Paragraphs

Consecutive lines of text are formatted as a single paragraph. As a block level element, you must to add a blank line after it to separate it from other block-level elements.

~~~~~~~
This is a paragraph.

This is as well.
~~~~~~~

Renders as:

{% highlight html %}
<p>This is a paragraph.</p>
<p>This is as well.</p>
{% endhighlight %}

###Headings

There are multiple ways to format headings in Kramdown. The easiest is to preceed the heading with hash characters (**#**) equal to the heading level. An `h1` for example, would be written as `#heading 1`. 

~~~~~~~
# This is a heading 1

## This is a heading 2

### This is a heading 3
~~~~~~~

Renders as:

{% highlight html %}
<h1>This is a heading 1</h1>
<h2>This is a heading 2</h2>
<h3>This is a heading 3</h3>
{% endhighlight %}

###Blockquotes

Blockquotes are formatted using the “greater than” character (**>**) at the start of the blockquote. Text inside a blockquote is wrapped with a paragraph. 

~~~~~~~
> This is a blockquote.
~~~~~~~

Renders as:

{% highlight html %}
<blockquote>
  <p>This is a blockquote.</p>
</blockquote>
{% endhighlight %}

###Ordered Lists

To create an ordered list, simply type a list started by a number followed by a period. Each list item should be on a separate line. Nested lists are created by indenting a list underneath an existing list item.

~~~~~~~
1. This is the first item
2. This is the second item
3. This is the third item
    1. This is a nested list
    2. More nested list
4. This is the fourth item.
~~~~~~~

Renders as:

{% highlight html %}
<ol>
    <li>This is the first item</li>
    <li>This is the second item</li>
    <li>This is the third item
        <ol>
            <li>This is a nested list</li>
            <li>More nested list</li>
          </ol>
    </li>
    <li>This is the fourth item.</li>
</ol>
{% endhighlight %}

###Block-level attributes

Often you may wish to assign attributes to block-level elements. To do this, follow the element with a *block inline attribute list* (block IAL). A block IAL consists of a left curly brace, followed by a colon, the attribute definitions and a right curly brace. 

~~~~~~~
# Apply the class “main” to this heading
{: .main}
~~~~~~~

Renders as:

{% highlight html %}
<h1 class="main">Apply the class “main” to this heading</h1>
{% endhighlight %}

Classes are applied with the syntax `.className` and IDs with `#ID-name`. For any other attribute you simply write the desired syntax:

~~~~~~~
# Another heading with the ‘role’ attribute applied
{: role="banner"}
~~~~~~~

Renders as:

{% highlight html %}
<h1 role="banner">Another heading with the ‘role’ attribute applied
</h1>
{% endhighlight %}

For multiple attributes, create a space-separated list inside the blockIAL.

~~~~~~~
# This heading has two classes and one ID applied
{: .class1 .class2 #ID-1}
~~~~~~~

Renders as:

{% highlight html %}
<h1 class="class1 class2" id="ID-1">This heading has two classes and one ID applied</h1>
{% endhighlight %}

###Inline formatting

Emphasis can be added to text by surrounding the text with either asterisks or underscores. This will result in wrapping the content in either the `strong` or `emphasis` tag depending upon how many are used:

~~~~~~~
I want to wrap **this text** in a strong tag and *this text* in an emphasis tag.
~~~~~~~

Renders as:

{% highlight html %}
<p>I want to wrap <strong>this text</strong> in a strong tag and <em>this text</em> in an emphasis tag.</p>
{% endhighlight %}

###Links

You can create a link by surrounding the text with square brackets and then directly following it with the link URL in parentheses. To add a title attribute, add the desired title in straight quotes (" ") after the link URL.

~~~~~~~
I usually search using [Google](https://www.google.com "Google").
~~~~~~~

Renders as:

{% highlight html %}
<p>I usually search using <a href="https://www.google.com" title="Google">Google</a>.</p>
{% endhighlight %}

###Images

Images are similar to links, but use an exclamation mark before the square brackets. The link text will become the alternative text of the image and the link URL specifies the image source.

~~~~~~~
![My dog](/images/Baxter.jpg)
~~~~~~~

Renders as:

{% highlight html %}
<img src="/images/Baxter.jpg" alt="My dog">
{% endhighlight %}

As you can see, Markdown is simple to write, and once you’ve learned the basic formatting options, generating semantic HTML is fairly simple. One of the most powerful Markdown features is the ability to nest HTML directly inside a Markdown document. That way if you’re unable to use Markdown to get exactly the HTML you need, you can simply inject HTML into the document and then continue using Markdown.

For more information on Kramdown and for a more complete reference, visit Kramdown’s [project page](http://kramdown.gettalong.org/index.html "Kramdown").





