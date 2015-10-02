---
layout: post
title:  "Basic Commands"
date:   2015-04-30
tags: [jekyll, terminal]
---
To control Jekyll you’ll run a series of commands within your command-line interface. The Jekyll gem gives you the `jekyll` executable, which has several commands and options you can use to build and serve your site. Let’s explore these commands and their options:

###build

{% highlight bash %}
$ jekyll build
#  The current directory will be generated into ./_site

$ jekyll build --destination <destination>
#  The current folder will be generated into <destination>

$ jekyll build --source <source> --destination <destination>
# The <source> folder will be generated into <destination>
{% endhighlight %}

Build does just that; it takes the contents of the current directory and generates it into the destination directory. If that directory is not specified, it defaults to the `_site` directory inside the current directory. Both the source and destination directories can be passed as options, just provide the path to the directory after the option.

###doctor

{% highlight bash %}
$ jekyll doctor
#  Checks for URL conflicts
{% endhighlight %}

The `doctor` command checks your site for URL conflicts, errors with your permalinks, and deprecation warnings. This can be especially useful if you’ve moved pages around or reorganized your site.

###help


{% highlight bash %}
$ jekyll help
# Generates help documentation
{% endhighlight %}


The `help` command generates a small help document that lists the current version of Jekyll, and reviews available commands and their options.  

###new

{% highlight bash %}
$ jekyll new <path>
#  Generates new site scaffold in targeted directory

$ jekyll new .
#  Generates new site scaffold in current directory

$ jekyll new --blank <path>
#  Generates basic site scaffold with empty directories and files
{% endhighlight %}

The `new` command generates a default Jekyll site in the specified directory. This is an extremely useful way to understand how Jekyll works, as you can explore and modify the default site. It’s also a great way to jump-start development, since many of the files and directories you need to create a Jekyll site will be created for you. The `blank` option creates a minimal directory structure with no files and an empty index file.

###serve

{% highlight bash %}
$ jekyll serve
# Builds site and serves it at http://localhost:4000/

$ jekyll serve --detach
# Same as `jekyll serve` but will detach from the current terminal.

$ jekyll serve --no-watch
# Same as `jekyll serve` but will not watch for changes or autoregenerate site.
{% endhighlight %}

The `serve` command generates the site and launches a built-in development server that allows you to preview your site. In its default option the server watches the source directory. Any changes made to source files will result in the server automatically regenerating those files and updating the site locally. To preview your site browse to http://localhost:4000/ unless you’ve specified a different base URL, in which case you’ll add that to the end of localhost:4000.
