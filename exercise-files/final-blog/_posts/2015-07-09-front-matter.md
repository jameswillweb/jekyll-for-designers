---
layout: post
title:  "YAML front matter"
date:   2015-07-09
tags: [jekyll, web design, yaml]
---
YAML front matter is perhaps the most important aspect of creating sites through Jekyll. It allows you to control how Jekyll processes and builds pages, create page-specific variables, and triggers file processing. Let’s take a closer look at front matter and how it can help you create more efficient Jekyll sites.

The front matter must be the first item in a file and must take the form of valid YAML set between triple-dashed lines. Here is a basic example:

{% highlight yaml %}

---
layout: default
title: Welcome to Jekyll
date: 2015-08-15 12:34
author: James Williamson
---

{% endhighlight %}

In this example Jekyll is instructed to use the **default.html** template for the content, and page variables for both the **title** of the page and the **author** are created. These can be written to the page using the `page.title` and `page.author` objects. A **date** for the page is given as well, and when used for a Post this will override the date used in the name of the post.

There are many predefined Global variables that you can set in the front matter of a page or post. These are:

layout
: Specifies which template to use for the content. As such it must point to a file in the **_layouts** directory. Do not add the file extension to the template name. To reference the **post.html** template you would add `layout: post`.

permalink
: Sets the permalink for the targeted file and is used to overwrite the default permalink style for a post. For example, the setting `permalink: /blog/:title` would overwrite the site permalink settings and locate the post at **/blog/post-title/index.html**.

published
: A boolean value that you can set to **false** if you don’t want the post published as the site is generated.

category
categories
: Assigns a single category or space-separated list of categories to a post. Categories can be used in permalinks and are hierarchical in nature. Allows you to structure posts like **web-design/html/post-title/index.html**. Posts can also be organized and sorted by categories. 

tags
: Similar to categories, you can apply a single tag or multiples tags in a YAML list or a space-separated string. Although posts can be organized and sorted by tags, they can’t be used for permalinks like categories. 

###Custom variables

In addition to the predefined Global Variables, you can create any custom variable you want. That variable can then be accessed by any page or post that uses that content. 

The most common form of custom variable is to store information like page titles, author names, and descriptions that can be added to the page or in **meta** tags to enhance page metadata. You can take this even further and control things like page layout as well. Let’s say that most pages in your site uses a simple sidebar, but occasionally you need to use a longer sidebar. In your template you could have the following markup:

{% highlight liquid %}
{{"{% if page.sidebar-long "}}%}
    {{"{% include sidebar-long.html "}}%}
    {{"{% else "}}%}
    {{"{% include sidebar.html "}}%}
{{"{% endif "}}%}
{% endhighlight %}

Now in any page or post that uses this template all you would need to add is the following variable to the front matter:

~~~~~~~
sidebar-long: true
~~~~~~~

Combining includes, templates, and front matter variables gives you an incredible amount of control over how pages are built, and limits the amount of variations you need in the form of templates.

You can even get to the point where you are generating entire pages with nothing but front matter. Let’s say you want to generate a single page for every tag that lists all posts tagged with that specific tag. You could create a template that generates everything dynamically based on the tag name. To create a new tag page, you simply name the file **tag-name.md** and add the following to the front matter:

{% highlight yaml %}

---
layout: tag-page
title: Tagged with Jekyll
tag: Jekyll
permalink: /tags/:title
---

{% endhighlight %}

The rest of the file could be empty and Jekyll would dynamically generate the page based on the tag name.

###SASS and CoffeeScript

Jekyll provides built-in support for Sass and CoffeeScript, but won’t process those files automatically. To enable those files for processing, add an empty front matter region to the top of the page:

~~~~~~~
---
---
~~~~~~~

The files will then be processed, and the resulting file will be located in the same directory in the generated site. The file **css/layout.scss** would generate **css/layout.css** in the finished site.

