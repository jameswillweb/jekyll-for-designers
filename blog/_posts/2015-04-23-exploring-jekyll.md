---
layout: post
title:  "Exploring Jekyll"
date:   2015-04-23
tags: [jekyll, web design, terminal, blogging]
---
Once Jekyll is installed you can begin to explore its functionality. In this post we’ll take a closer look at Jekyll’s default boilerplate site and discuss how you can use it to learn more about Jekyll.

The first step to exploring Jekyll is to create a new Jekyll site, serve it, and then preview it locally in your browser. Then you can begin to tweak the site to get a better understanding of how it all works together. 

###Building a new site

To build a new site, create a directory named `practice` and navigate there in Terminal or whichever command line interface you’re using. Once there run the following commands:

{% highlight bash %}
$ jekyll new explore
# Creates the directory explore and builds a new boilerplate site inside it

$ cd explore
# Navigates to explore, making it the current directory

$ ls
# Lists the files and directories of the current site
{% endhighlight %}

You should see a list of files and directories that were created inside your new **explore** directory. A closer examination would reveal a structure similar to this:

~~~~~~~
|---_config.yml
|---_includes
    |---footer.html
    |---head.html
    |---header.html
|---_layouts
    |---default.html
    |---page.html
    |---post.html
|---_posts
    |---2015-08-23-welcome-to-jekyll.markdown
|---_sass
    |---_base.scss
    |---_layout.scss
    |---_syntax-highlighting.scss
|---about.md
|---css
    |---main.scss
|---feed.xml
|---index.html
~~~~~~~

Some highlights: The **_config.yml** file contains the configuration settings for the blog, the **_includes** folder holds HTML snippets that are used to generate page regions, the **_layouts** directory contains the templates used to assemble individual pages, and the **_posts** folder holds the markdown files for individual posts. The **about.md** and **index.html** are individual pages, found on the root of the site. Note that pages can be created either using HTML or markdown. 

Feel free to open any of the files in a text editor and explore them; just don’t make any changes yet! 

###Serving your new site

Now run the following command:

{% highlight bash %}
$ jekyll serve
# Builds the site in the _site directory and serves it at http://localhost:4000
{% endhighlight %}

If you examine your directory structure you’ll now find a **_site** directory that contains the generated site. Open up a browser and navigate to http://localhost:4000. Click through the site, explore the default post and note the default information. Using a text editor, open the markdown post in the **_posts** directory. At the top of the file you’ll see the YAML front matter contained between the dashed lines. Change the title to “Exploring Jekyll.” Save the file and note in the Terminal window that the Jekyll server detects the change and regenerates the file. Refreshing the file in your browser should reflect the change you made to the default post. 

Not all changes are automatically regenerated. Open the **_config.yml** file in your text editor. Change the title of the site to “Working with Jekyll” and replace the placeholder contact information with your contact info and then save the file. Notice that the Jekyll server doesn’t automatically detect the change. Stop the server by typing `CTRL+C` in the Terminal window. Run the `jekyll serve` command again and refresh the page in your browser. You should now see your updated information.

From here begin to experiment with making changes to templates, adding posts, and modifying the overall site configuration. This is a practice site, so it’s totally okay to break it! By exploring and experimenting with the Jekyll boilerplate site you can get a better sense of how Jekyll works and how your own site should be structured.

