---
layout: post
title: How to Build Minimalist Blog with Jekyll Hosted on GitHub Pages
comments: true
---

Last November I finally made up my mind to start my own journey of blogging. I was searching for the right technology for building blogs at that time. My goal was to run my own website with minimal efforts to manage the website itself, kind of Blog-As-A-Service thing. Then I found [GitHub Pages]() hosted [Jekyll]() website looks like a good choice for me.

### So What is Jekyll?

Here is what they say about themselves on [Jekyll's github]():

>[Jekyll]() is a simple, blog-aware, static site generator perfect for personal, project, or organization sites. Think of it like a file-based CMS, without all the complexity. [Jekyll]() takes your content, renders [Markdown]() and Liquid templates, and spits out a complete, static website ready to be served by Apache, Nginx or another web server. [Jekyll]() is the engine behind [GitHub Pages](), which you can use to host sites right from your GitHub repositories.

From my experience and point of view, there are a few reasons why you might consider using Jekyll over other platform:
* Simplisity - no database nor server-side language needed, only your content (in Markdown or Textile) and CSS. This saves your tons of trouble of dealing with server-side issues.
* Static Site - Jekyll compile your content into static site before deployment. Static content instantly gives you massive scalability almost for free. If scalability is important for your site, static site technology might be a good idea.
* Free Hosting with [GitHub Pages]() - [GitHub Pages]() hosted your open sourced site for free, even on a custom domain name.
* Customization - All the plugins you asked for, such as [Pagination](), [Permalinks](), [Templating]() and more.

### How to Get Started

I came cross a minimalist style Jekyll theme Poole, which looks like a fairly good starting point to play with Jekyll. Poole is design and developed by @mdo to provide a clear and concise foundation setup for any Jekyll site. It does so by furnishing a full vinilla Jekyll install with example templates, pages, posts and styles.

##### Jekyll Setup and Dependencies

For **Linux/Mac** users, the best way to install Jekyll is via RubyGems. From terminal simply install jekyll from gem, all Jekyll's gem dependencies will be automatically installed.
```Bash
gem install jekyll
```

For **Windows** users, the catch is to make sure you have Ruby installed before installing Jekyll.
1. Install Chocolatey (if you don't already have it)
```PowerShell
iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
```
2. Install Ruby via Chocolatey
```PowerShell
choco install ruby -y
```
3. Install Jekyll from gem
```PowerShell
gem install jekyll
```

You can find the [quick-start guide](http://jekyllrb.com/docs/quick-start/) and [installation](http://jekyllrb.com/docs/installation/) instructions from Jekyll. This [article](https://davidburela.wordpress.com/2015/11/28/easily-install-jekyll-on-windows-with-3-command-prompt-entries-and-chocolatey/) has detailed instructions for install Jekyll on Windows you can refer to.

##### Jekyll Quick-Start

After installed Jekyll and its dependencies, now we are good to go. Simply create a new Jekyll site.
```PowerShell
jekyll new mysite
cd mysite
```
Now you can ready to serve this site and browse it at http://localhost:4000 locally
```PowerShell
jekyll serve
```
Yes, it *is* this simple.

### Site Layout

My blog is built by forking [Lanyon]() Jekyll theme, and here is the basic structure of my site, you can view it on [Github](https://github.com/dhei/dhei.github.io). Let me use it as an example to explain how Jekyll site actually works.

[]
 
* Directory [_posts]() contains all the blog posts in Markdown format. Jekyll also supports Textile and other markup formats.
* Drectory [_drafts]() contains drafts not yet published.
* Directory [_layouts]() and [public]() contains the absolutely essentiall parts - HTML templating pages and CSS required for this site. It's nothing fancy, just the minimal HTML/CSS required.
* Directory [_includes]() contains all the *extra* plugins necessary for my site, such as [Disqus] commenting system, and [Google Analytics]().
* Directory [assets]() contains my media files including images.
* [_config.yml]() is the Jekyll's configuration in [yml]() format.
* [CNAME]() is where you configure your custom domain name, for instance: `diheiblog.com`






