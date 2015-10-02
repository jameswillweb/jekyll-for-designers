---
layout: post
title:  "Deployment Options"
date:   2015-08-01
tags:  [jekyll, deployment, github pages, git]
---
Once you’ve finished building your Jekyll site you’ll need to decide where and how you want to deploy it. Since Jekyll builds static content you can serve it almost anywhere. There are no server-side dependencies, CMS installations, database administrators, or server stacks to worry about. If the server can handle HTML, CSS, and JavaScript, it can serve your site. With that in mind let’s take a look at some of the most common options for deploying Jekyll sites.

###FTP/SFTP

Almost all hosting companies allow you to upload content via FTP or SFTP. Simply use a FTP client (such as [Filezilla](https://filezilla-project.org/ "Filezilla")) to upload the contents of your **_site** directory to the **www** or **public_html** directory of your hosting server. One downside to this method is the manual nature of updating your site. When files change you’ll need to manually overwrite your remote files. For larger sites this can be time-consuming and prone to errors. 

One option for enhancing FTP deployment is to use a Git-integrated FTP client like [git-ftp](https://github.com/git-ftp/git-ftp "git-ftp"). This allows you to bring version control into your deployment workflow and only upload the files that have changed.

###Git

Speaking of Git, if you’re using it to source-control your site, you can set it up to push to your web server when it’s time for deployment. To do this you’ll need to set up a post-update hook on your remote server. You’ll also, of course, need Git installed on your server and SSH access. This method of deployment is a little more technical than others, so you’ll need to be comfortable with Git, the command line interface, and writing basic scripts. [Nicolas Gallagher wrote one of the best posts](http://nicolasgallagher.com/simple-git-deployment-strategy-for-static-sites/ "Git for static sites") on the subject that I’ve seen, though a quick Google search will return several articles detailing versions of this workflow.

###Deployment Web Services

Several online services offer deployment workflows for apps and sites. Most offer tiers of services that range from free to monthly fees based on the size and number of sites you’ll be updating. While many of their services aren’t really necessary for smaller static sites, the convenience of having your deployment automated with a single click is pretty nice, and the extra features can come in handy as your site grows. Check out [Beanstalk](http://beanstalkapp.com/ "Beanstalk"), [DeployBot](http://deploybot.com/ "Deploybot"), [Netlify](https://www.netlify.com/ "Netlify") and [Travis CI](https://travis-ci.org/ "Travis CI") for a good idea of how these services work and if they’re right for you.

###Github

Github uses Jekyll to power it’s Github Pages feature, so it’s only natural that deploying Jekyll sites through Github is quick and easy. You can even host your personal or project site for free on Github. You have two options for serving your site: user/organization or as a project page. Each Github user gets one free user/organization Github Pages site, and unlimited project pages. Organization pages are served as the “home” site for the user, so it’s served at `username.github.io.` Project pages are served as subdomains, so they would be served at `username.github.io/project-name.` The only real difference between the two methods is how you format relative links, as project pages have the project name directory as part of their base URL. You can even redirect a custom domain to your Github Pages site, which makes it a very attractive choice for hosting personal blogs and smaller sites.

The workflow for deploying to Github Pages is simple. Login to your Github account, create a new repo, and then point your local repo to use the new Github repo as its remote. Create a new branch called `gh-pages` and push everything except the **_site** directory to your new Github repo. Github will detect the Jekyll site, build it, and serve the site at the appropriate URL. From there, updating the site is as simple as writing a new Markdown file and making a push. 

###More information

For more information on deploying Jekyll sites (and more options), check out the section on [deployment methods](http://jekyllrb.com/docs/deployment-methods/ "deployment methods") in Jekyll’s documentation. 

