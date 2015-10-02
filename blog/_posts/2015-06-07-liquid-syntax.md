---
layout: post
title:  "Liquid Syntax Basics"
date:   2015-06-07
tags: [liquid, jekyll, templates]
---
Jekyll uses the [Liquid](http://liquidmarkup.org/ "liquid") template language to control the logic of templates and assemble pages dynamically. To get the most out of Jekyll, and to build effective templates you need to understand the basics of how Liquid works. In this post we’ll cover the basics of Liquid syntax so that as you begin to author templates, you’ll have a greater understanding of Jekyll’s capabilities and how Liquid can help you build more powerful sites.

Liquid was created in 2006 as a Ruby template language for the ecommerce site [Shopify](https://docs.shopify.com/themes/liquid-documentation/basics "Shopify themes"). It remains an integral part of Shopify, but has been spun off for general use as well. 

Liquid uses a combination of **tags**, **objects**, and **filters** to load and format content. Within tags, logic can be applied to loop through objects, create variables, and apply conditional statements to control the building of content.

There are two basic types of markup in Liquid, **output** and **tags**. Output writes content to the page while tags perform some type of function, like looping through an array. Let’s explore output markup first.

###Output

Output writes content to the page. Output tags start with two curly braces, contain the content to be written to the page, and then end with two curly braces. Here’s an example:

{% highlight liquid %}
Written by {{"{{author"}}}}
Written by {{"{{page.author"}}}}
Written by {{"{{'james'"}}}}
{% endhighlight %}

In this instance the value of `author` would be evaluated and written to the page, the `page` object would be parsed to find the value of the `author` property and that would be written to the page, and then the literal string “james” would be written to the page.

Output markup can be further modified through the use of filters. Filters are methods that can be used to transform the results of the output tags. Filters appear to the right of the output parameter, and are separated using the ‘pipe’ character `( | )`.

Here’s a filter in action:

{% highlight liquid %}
{{"{{ site.time | date_to_string"}}}}
<!-- would output ‘22 Aug 2015’ -->
{% endhighlight %}

It’s also possible to use more than one filter at a time. Here are a few of the standard filters available in Liquid:

* date - reformat a date
* capitalize - capitalize words 
* downcase - convert a string to lowercase
* upcase - convert a string to uppercase
* first - get the first element of an array
* last - get the last element of an array
* join - join elements of an array with specific character between them
* sort - sort elements of an array
* size - return the size of an array or string
* strip_html - strip html from string
* strip_newlines - strip all newlines from string
* replace - replace each occurrence
* replace_first - replace the first occurrence 
* remove - remove each occurrence 
* remove_first
* truncate - truncate a string down to x characters.     
* truncatewords - truncate a string down to x words
* prepend - prepend a string
* append - append a string
* slice - slice a string. Takes an offset and length.

Filters are an incredibly powerful way to transform content within your templates. It’s important to understand how they work, and what their capabilities are, so that you can format content correctly as well as generate the desired output. For a full list of available filters and how they work, check out the [filter documentation](https://docs.shopify.com/themes/liquid-documentation/filters "filters") on the Shopify site.

###Tags

Liquid tags are functional, when applied they perform some type of action. They provide the basic programming logic for templates and allow you to build intelligent templates that can respond to a number of different factors. Tags are written with a curly brace followed by a percentage sign (*%*), contain the desired instructions, and end with a percentage sign and a curly brace. Tags usually come in twos, with an opening tag and a closing tag that wraps the targeted content. Here’s an example:

{% highlight liquid %}
{{"{% if page.title == 'About' "}}%}
    About this blog
{{"{% endif "}}%}
{% endhighlight %}

In this example Jekyll would check the current page title. If the value is “About” then the text “About this blog” will be written to the page. 

Tags are organized in four distinct categories; Control Flow, Iteration, Theme, and Variables. Control Flow tags are used to apply conditional logic, such as **if/else** statements. Iteration tags allow you to loop through code and run code repeatedly. They contain tags like **for loops** and **cycles**. Theme tags are typically template-specific tags and allow you to output specific markup, add comments, control arrays, and handle pagination.

Here’s a sample of some of the more commonly used tags in templates:

###for loops

{% highlight liquid %}
    {{"{% for post in site.posts "}}%}
      <li>
	  <a href="{{"{{ post.url "}}}}">{{"{{ post.title "}}}}</a>
      </li>
{{"{% endfor "}}%}
{% endhighlight %}

Loops over collections, executing code for as long as the conditions within the loop lasts. In this example Jekyll would loop through all posts in the site and for each one create a list item that contains a link to that specific post via its URL and title. Note the use of output tags within the **for** loop.

###if/else statements

{% highlight liquid %}
  {{"{% if paginator.previous_page "}}%}
     <a href="{{"{{ paginator.previous_page_path "}}}}">Previous</a>
  {{"{% else "}}%}
    <span>No previous posts</span>
  {{"{% endif "}}%}
{% endhighlight %}

Allows the application of conditional logic within templates. In this example Jekyll would check to see if there are any posts older than the current one using the **paginator** object. If so, a link would be created to the previous posts. If not a message is created stating that there are no previous posts. There are many variations on the if/else statements syntax including `elseif`, `unless`, and `case` statements. 

###includes

{% highlight liquid %}
  {{"{% include footer.html "}}%}
 {% endhighlight %}

Inserts the included content at the desired location. In this example the contents of the file “footer.html” would be inserted at the location of the tag. Allows for the dynamic insertion of content.

###variables

{% highlight liquid %}
  {{"{% assign author = 'james' "}}%}
  {{"{{ author "}}}}
 {% endhighlight %}

There are two main ways to assign variables using Liquid. The **assign** method shown above assigns a literal string which is then stored for later use.

{% highlight liquid %}
  {{"{% capture site_tags "}}%}
      {{"{% for tag in site.tags "}}%}{{"{{ tag | first "}}}}
           {{"{% unless forloop.last "}}%},{{"{% endunless "}}%}
      {{"{% endfor "}}%}
  {{"{% endcapture "}}%} 
{% endhighlight %}

The **capture** method, shown above, captures the values inside of the opening and closing tags and stores it in a string. In the example shown Jekyll would loop through all tags in the site, pull each one out, and separate them with a comma. The resulting variable “site_tags” would contain a comma-separated list of all tags within the site.

Tags give you the ability to create templates that generate dynamic templates using intelligent logic. For more information on them, and for a complete list of available tags, check out the [Liquid documentation](https://docs.shopify.com/themes/liquid-documentation/tags "tags documentation") on tags.


