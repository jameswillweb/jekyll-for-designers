---
layout: post
title:  "Welcome to Jekyll!"
date:   2015-02-15
tags: [jekyll, web design, blogging, yaml, liquid]
---

Welcome to the companion site for the [lynda.com](http://www.lynda.com "lynda.com") course *Jekyll for Web Designers*. This course is designed to present Jekyll to web designers in a clear, concise way. In this post we’ll take a quick look at how Jekyll works, and whether it’s right for you. 

[Jekyll][1] bills itself as “a simple, blog-aware, static site generator.” It takes source files like templates, stylesheets, includes, and posts and uses them to generate a website that can then be hosted on your server of choice. This means that the entire website is generated at once, and visitors are simply served static files. This can be much faster than blogging platforms like WordPress, which use a CMS to generate pages as they’re requested. [This blog]({{site.baseurl}}/index.html "articles"), for example, was generated from a series of templates, posts, html snippets, and CSS using Jekyll.

>When you remove layers, simplicity and speed happen.
<cite>&mdash; Ginni Rometty</cite>

Although Jekyll is built to be “blog aware,” it’s important to point out that it is not blogging software in the traditional sense. It’s simply a parsing engine that builds what you put into it. This means that while you have total control over every aspect of your site, you also have to build everything as well. That may sound daunting at first, but once you get the hang of how it works you can quickly and easily start building Jekyll-driven sites.

###How Jekyll works

Jekyll is a Ruby-based parsing engine that uses [YAML](http://yaml.org/ "YAML"), the [Liquid Templating language](http://liquidmarkup.org/ "liquid"), and [Markdown](http://daringfireball.net/projects/markdown/ "markdown") to assemble content into HTML. That might sound confusing at first, but it’s really pretty simple. YAML is used to store data, site variables, and what is known as “front matter,” which drives things like the layout used for a post or page. Liquid is used to build the templates that pages are built from, and Markdown can be used to format content for individual posts or pages. You can also use regular HTML to format content as well, but Markdown makes writing content much more natural. This post, for example, was written in Markdown.

A simple Jekyll directory looks like this:

~~~~~~~
├── _config.yml 
├── _includes 
|   ├── footer.html 
|   └── header.html 
├── _layouts 
|   ├── default.html 
|   └── post.html 
├── _posts 
|   ├── 2015-07-29-my-second-post.md 
|   └── 2015-06-15-my-first-post.md
├──css 
|   ├── main.css  
├── _site  
└── index.html
~~~~~~~

The **_config.yml** file is a YAML file that contains the overall site configuration such as site title, author information, pagination, and permalinks. The **_includes** directory holds HTML snippets that can be injected on any desired page with a simple Liquid tag. The **_layouts** folder contains the HTML templates that are used to generate pages for the site, and the **_posts** directory contains the individual blog posts, written in either Markdown or HTML. Note the naming convention for the posts. This is used to date stamp the posts and can be used for site organization and permalinks. The **css** directory contains the CSS for the site, and in this case is not preceded by an underscore. Any directory without an underscore is not parsed, and is copied as-is when the site is generated. Jekyll also supports SASS, any **.scss** files with YAML front matter would be parsed and processed. The **_site** directory is where the generated site will be created. From there it can be uploaded to your server of choice. Finally the **index.htm** file contains the content and blogging logic for the home page of the blog, and typically uses one of the templates for overall page structure.

In addition to the Liquid tags, Jekyll uses YAML front matter to guide the creation of pages. A post, for example, might have this YAML front matter at the top of the page:

~~~~~~
---

layout: post

title: "My First Post"

category: jekyll

---
~~~~~~

This tells Jekyll to use the “post” template to assemble the page, and assigns the ‘title’ and ‘category’ variables that can be used on that page or throughout the site. Jekyll will process any file that contains YAML front matter. The front matter must be the first thing in the file and must take the form of valid YAML set between triple-dashed lines. It can contain any of the predefined global variables such as **layout**, **permalink**, or **category** or any custom variable you wish to create. If you wished to display the authors name, for example, you could add **author: ‘author’s name’** to the front matter and then reference that in your templates using `{{"{{page.author"}}}}`.

###Is Jekyll right for you?

Jekyll isn’t right for every designer, or every project. It’s perfect for smaller sites, blogs, portfolios, and project wikis, but might not be right for corporate sites or sites that require advanced functionality and heavy database usage. 

Here are a few things to consider when considering Jekyll:

**Comfort level with the command line.** Jekyll is built in Ruby and uses a command line interface. You don’t need to be a hard-core developer to use it, but you will need to make sure you can properly install Jekyll and it’s dependencies. From there most of the tasks you’ll perform with Jekyll are controlled from the command line. For the most part the commands are pretty simple, so don’t let this scare you off; just keep it in mind as you consider Jekyll.

**Complexity level.** Jekyll is simplicity itself. You’re responsible for all the HTML, CSS, and JavaScript in your site. Unlike a CMS platform like WordPress there are no themes or existing site architecture to get in the way. Personally I love this level of control, but some designers like a bit more out of the box.

**Hosting requirements.** This is where Jekyll really shines. Being a static site generator means that all site generation occurs locally in the development environment. The resulting site can then be uploaded and hosted almost anywhere, as there are no requirements for database administration or server side code support. Jekyll is also the engine behind Github Pages, and integration with Git and Github is tight. You can even host your Jekyll blog for free on Github Pages. Once it’s set up publishing is as simple as writing a new post and making a commit.

**Speed and security.** Since you’re serving static HTML, CSS, and JavaScript assets, Jekyll is typically faster than CMS-driven sites. Security is easier as well, as there’s no server-side administrator, database, or server-side code to hack into.

**Data requirements.** Working with data in Jekyll is fairly basic. Data is typically stored in a YAML file in a fashion similar to JSON and referenced using Liquid tags. Advanced data requirements can be tricky and require a fair amount of extra work. If you need database functionality, or make heavy use of user data Jekyll might not be the best choice for you.

**Extensibility.** Jekyll’s community is only a fraction of the size of WordPress or other CMS communities. As such, there aren’t as many plugins or add-ons for Jekyll as there are for other platforms. In many cases if you want to add functionality not included in the default jekyll build you’ll need to do it yourself. For security reasons Github Pages doesn’t allow plugins, so if you want to add plugins to a Github hosted site you’ll need to do some pretty painful workarounds. 

I highly recommend checking out Jekyll and giving it a try, it might just be the tool you’re looking for. For a high-level view of Jekyll check out Tom Preston-Werner’s [post announcing the creation of Jekyll](http://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html "blog like a hacker"). It will give you a better understanding of the philosophy behind Jekyll and how it works. To dig deeper into Jekyll check out the [Jekyll project page][1] and [documentation][2].

 [1]: http://jekyllrb.com/ "jekyll"
 [2]: http://jekyllrb.com/docs/home/ "jekyll documentation"
