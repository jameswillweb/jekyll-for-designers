---
layout: post
title:  "Configuration Options"
date:   2015-05-14
tags: [jekyll, yaml, markdown]
---
One of the main reasons to use a static site generator like Jekyll is the automation it provides for repetitive tasks and page generation. In Jekyll many of those automations are driven by the configuration file **_config.yml**. In order to harness the true power of Jekyll it’s important to understand how this file works and what your options are when using it.

The **_config.yml** sits in the root of your source directory and, as the name suggests, controls the configuration options for your site. Let’s break down the options in the sample **_config.yml** that’s created when you generate a new Jekyll site before moving on to covering the Global config options.

~~~~~~~
# Site settings

title: Your awesome site
email: your-email@domain.com
description: > # this means to ignore newlines until "baseurl:"
    Write an awesome description for your new site here.
    You can edit this line in _config.yml. It will appear
    in your document head meta (for Google search results)
    and in your feed.xml site description.
baseurl: "" # the subpath of your site, e.g. /blog/
url: "http://yourdomain.com" # the base hostname & protocol for your site
twitter_username: jekyllrb
github_username:  jekyll

# Build settings

markdown: kramdown
~~~~~~~

The important thing to note here is that they’ve split the configuration options into two sections, site settings and build settings. All of the site settings other than **baseurl** and **url** are basically site variables that can be reused throughout the site. As such, they are all optional. Storing the **title** of the site in a variable, for instance, makes it easy to set the title element for pages, or to use it in a heading element on a page. By setting these variables in the **_config.yml** file they are available to any page throughout the site. You could access the title, for example, by using the Liquid tag `{{"{{site.title"}}}}`.

There is a difference between the `site.url` and `site.baseurl` objects and when you need them. By default, the `site.url` variable is used in the page head for things like canonical links and links to the RSS feed that are accessed by external systems, although it can be used to create absolute links within your site.

The `site.baseurl` variable indicates the root folder of your site. By default it is set to " " (empty string), which indicates your site is hosted at the root of http://yourdomain.com. However, if your site is located in http://yourdomain.com/blog, you have to set `site.baseurl` to **/blog** (note the slash). This will allow you to create relative links to assets that load correctly.

When creating your own site, you should give careful consideration to what type of information to store in your **_config.yml** file. Being able to access this data at any time throughout your site is a powerful option.

Below the site settings the default config file contains a section for “build settings.” Even though they only include a single option here, this section hints at the fact that you can use the  **_config.yml** file to control much of the site’s serve and build options. The lone option here instructs Jekyll to use Kramdown as its Markdown converter. Here are a few other options you can use when controlling the serve and build processes:

###local port

~~~~~~
port: PORT
~~~~~~~

Listen to the given port. 4000 is the default.

###base URL

~~~~~~
baseurl: URL
~~~~~~~

Serves the website from the given base URL, for example **/blog** would serve the home page from the blog subdirectory. Can be used to construct URLs throughout the site as well.

###source

~~~~~~
source: <directory>
~~~~~~~

Sets the directory Jekyll uses as the root directory for building files. By default it’s the current directory that the `build` command is run in.

###destination

~~~~~~
destination: <directory>
~~~~~~~

Sets the directory where Jekyll writes the built site. By default Jekyll creates a `_site` directory in the `source` directory.

###exclude

~~~~~~
exclude: [DIR, FILE, ...]
~~~~~~~

Lists files and directories to exclude from the build process. Useful for source asset files like .psd files and other files that are not part of the build process or final site.

###include

~~~~~~
include: [DIR, FILE, ...]
~~~~~~~

Lists files and directories that are copied over to the finished site regardless of their filetype or extension. Dotfiles, for example, are excluded from the build, so you could force the inclusion of a .gitignore or .htaccess file. The default value for `include` contains .htacess.

###keep

~~~~~~
keep_files: [DIR, FILE, ...]
~~~~~~~

During the build process the destination folder is wiped clean before the site is regenerated. If you have files or directories in the destination folder that are not part of the build process this setting can preserve those files. Useful for favicon files or other site assets that are unlikely to change and not controlled by Jekyll.

###encoding

~~~~~~
encoding: ENCODING
~~~~~~~

Sets the encoding used for files. The default is utf-8.

###permalink

~~~~~~
permalink: [options]
~~~~~~~

Specifies the permalink style used for posts and controls the directory structure for generated posts. The default, `date`, results in the permalink /YEAR/MO/DATE/name.html. Therefore a post titled **2015-01-29-first-post.md** would have the permalink of /2015/01/29/first-post.html, and would be generated using that directory structure. For a full list of permalink options, see the [Jekyll documentation on permalinks](http://jekyllrb.com/docs/permalinks/ "permalinks").

###pagination

~~~~~~
paginate: [num]
~~~~~~~

Allows you to set the number of blog posts to display on the **index.html** page. This allows you to break your posts up and display them over a number of pages. For an overview of how pagination works, and how to also set the `paginate_path` option, see the [Jekyll documentation on pagination](http://jekyllrb.com/docs/pagination/ "pagination").

###More information

This is a brief look at some of the configuration options available for your **_confing.yml** file. For more information on configuration, and how to set global default options for pages, check the full [Jekyll documentation on site configuration](http://jekyllrb.com/docs/configuration/ "configuration").
