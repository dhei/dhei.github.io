---
layout: post
title: How to Build a Minimalist Blog with Jekyll Hosted on GitHub Pages
comments: true
---

Last November I finally made up my mind to start my own journey of blogging. I searched for the right technology for building blogs for a while. My goal was to run my own website with minimal efforts of managing the website itself, kind of *Blog-As-A-Service* thing I was expecting. Then I found [Jekyll](http://jekyllrb.com/) website hosted on [GitHub Pages](https://pages.github.com/) looks quite appealing to me.

So I built my first [blog](http://diheiblog.com) hosting on [GitHub Pages](https://pages.github.com/) with [Jekyll](http://jekyllrb.com/) within hours. I really like Jekyll and it deserves a blog post about it.

## So What is Jekyll?

![](/assets/images/jekyll-logo-light-solid.png)

Here is what they say about themselves on [GitHub](https://github.com/jekyll/jekyll):

>Jekyll is a simple, blog-aware, static site generator perfect for personal, project, or organization sites. Think of it like a file-based CMS, without all the complexity. Jekyll takes your content, renders [Markdown](https://en.wikipedia.org/wiki/Markdown) and [Liquid](https://github.com/Shopify/liquid) templates, and spits out a complete, static website ready to be served by Apache, Nginx or another web server. Jekyll is the engine behind GitHub Pages, which you can use to host sites right from your GitHub repositories.

From my point of view, there are a few reasons why you might consider using Jekyll over other platform:

* **Simplisity** - no database nor server-side language needed, only your content (in [Markdown](https://en.wikipedia.org/wiki/Markdown) or [Textile](https://en.wikipedia.org/wiki/Textile_(markup_language))) and CSS. This saves your tons of trouble of dealing with server-side issues.

* **Static Site** - Jekyll compile your content into static site before deployment. Static content instantly gives you massive scalability almost for free. If scalability is important for your site, static site technology might be a good idea.

* **Free Hosting on GitHub Pages** - [GitHub Pages](https://pages.github.com/) hosted your open sourced site for free, even on a custom domain name.

* **Customization** - All the plugins you asked for, such as [Pagination](http://jekyllrb.com/docs/permalinks/), [Permalinks](http://jekyllrb.com/docs/permalinks/), [Templating](http://jekyllrb.com/docs/templates/) and [more](http://jekyllrb.com/docs/plugins/).

## How to Get Started

I came cross a minimalist style Jekyll theme [Lanyon](https://github.com/poole/lanyon), which looks like a fairly good starting point to play with Jekyll. [Lanyon](https://github.com/poole/lanyon) is design and developed by [@mdo](https://twitter.com/mdo) to provide a clear and concise foundation setup for any Jekyll site. It does so by furnishing a full vanilla Jekyll install with example templates, pages, posts and styles.

#### Jekyll Setup and Dependencies

For *Linux/Mac* users, the best way to install Jekyll is via RubyGems. From terminal simply install jekyll from gem, all Jekyll's gem dependencies will be automatically installed.

```
gem install jekyll
```

For *Windows* users, the catch is to make sure you have Ruby installed before installing Jekyll.

1.Install Chocolatey (if you don't already have it)

```
iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
```

2.Install Ruby via Chocolatey

```
choco install ruby -y
```

3.Install Jekyll from gem

```
gem install jekyll
```

You can find the [quick-start guide](http://jekyllrb.com/docs/quick-start/) and [installation](http://jekyllrb.com/docs/installation/) instructions from Jekyll. This [article](https://davidburela.wordpress.com/2015/11/28/easily-install-jekyll-on-windows-with-3-command-prompt-entries-and-chocolatey/) has detailed instructions for install Jekyll on Windows you can refer to.

#### Jekyll Quick-Start

After installed Jekyll and its dependencies, now we are good to go. Simply create a new Jekyll site.

```
jekyll new mysite
cd mysite
```

Now you can ready to serve this site and browse it at [http://localhost:4000]() locally

```
jekyll serve
```

Yes, it *is* this simple.

#### Hosting on GitHub Pages

Now you want to deploy your Jekyll site to Github Pages to take advantages of their free hosting. You can follow GitHub Pages instructions [here](https://pages.github.com/). You simply create a new repository named `{your-github-alias}.github.io`, commit and push your changes to GitHub. Your Jekyll site will go alive on `http://{your-github-alias}.github.io` in seconds.

Congratulations, you just created and deployed your Jekyll blog hosted on GitHub Pages.

## Jekyll Site Layout

My blog is built by forking [Lanyon](https://github.com/poole/lanyon) repository, and here is the basic structure of my site, you can view it on [Github](https://github.com/dhei/dhei.github.io). Let me use it as an example to explain how Jekyll site actually works.

![](/assets/images/my-github-repo-layout.jpg)
 
* Directory [_posts](https://github.com/dhei/dhei.github.io/tree/master/_posts) contains all the blog posts in Markdown format. Jekyll also supports Textile and other markup formats.
* Drectory [_drafts](https://github.com/dhei/dhei.github.io/tree/master/_drafts) contains drafts not yet published.
* Directory [_layouts](https://github.com/dhei/dhei.github.io/tree/master/_layouts) and [public](https://github.com/dhei/dhei.github.io/tree/master/public) contains the absolutely essentiall parts - HTML templating pages and CSS required for this site. It's nothing fancy, just the minimal HTML/CSS required.
* Directory [_includes](https://github.com/dhei/dhei.github.io/tree/master/_includes) contains all the *extra* plugins necessary for my site, such as [Disqus](https://disqus.com/) commenting system, and [Google Analytics](https://www.google.com/analytics/).
* Directory [assets](https://github.com/dhei/dhei.github.io/tree/master/assets) contains my media files including images.
* [_config.yml](https://github.com/dhei/dhei.github.io/blob/master/_config.yml) is the Jekyll's configuration in [YML](http://fdik.org/yml/) format.
* [CNAME](https://github.com/dhei/dhei.github.io/blob/master/CNAME) is where you configure your custom domain name, for instance: `diheiblog.com`

## Customization

##### Custom Domain Name
By default, your GitHub Pages hosted Jekyll site lives in `https://{your-github-alias}.github.io` domain under Github's domain. You wish to move your site to your own domain name. This is made super easy by Github Pages, the only thing you need to do is [adding a CNAME file in your root directory](https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages/).

##### Disqus Comments
[Disqus] comments system is very popular these days, and extremely easy to plug into your site. I decided to add Disqus to the default page by adding this line to [_layouts/post.html](https://github.com/dhei/dhei.github.io/blob/master/_layouts/post.html):

```
include comments.html
```

And created a [_includes/comments.html](https://github.com/dhei/dhei.github.io/blob/master/_includes/comments.html) to include JavaScript code given by Disqus:

{% highlight html %}
{% if page.comments %}
  <!-- Add Disqus comments. -->
  <div id="disqus_thread"></div>
  <script type="text/javascript">
    /* * * CONFIGURATION VARIABLES: EDIT BEFORE PASTING INTO YOUR WEBPAGE * * */
    var disqus_shortname = '<USERNAME>';
    var disqus_identifier = "{{ site.disqusid }}{{ page.url | replace:'index.html','' }}";
	
	// var disqus_developer = 1; // Local testing. Comment out when the site is live
	
	/* * * DON'T EDIT BELOW THIS LINE * * */
	(function() {
	  var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
	  dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
	  (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
	})();
  </script>
  <noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
  <a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>
{% endif %}
{% endhighlight %}

There is a catch in the above JavaScript code - you need `var disqus_developer = 1` line if you want Disqus work locally.

##### Google Analytics
I am completely new to [Google Analytics] and I found it's really simple to plug into your site. Like the way I add Disqus comments, it's a one line change to [_layouts/default.html](https://github.com/dhei/dhei.github.io/blob/master/_layouts/default.html):

```
include google_analytics.html
```


And created a [_includes/google_analytics.html](https://github.com/dhei/dhei.github.io/blob/master/_includes/google_analytics.html) to include JavaScript code given by Google:

{% highlight html %}
<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');
  ga('create', '<your-UA-id>', 'auto');
  ga('send', 'pageview');
</script>
{% endhighlight %}

## More Links

* Jekyll GitHub project [https://github.com/jekyll/jekyll]()
* Jekyll minimalist style theme Lanyon on [GitHub](https://github.com/poole/lanyon) with [demo](http://lanyon.getpoole.com/)
* Tutorial [Run Jekyll on Windows](http://jekyll-windows.juthilo.com/)
* Joshua Lande's tutorial [How I Created a Beautiful and Minimal Blog Using Jekyll, Github Pages, and poole](http://joshualande.com/jekyll-github-pages-poole/)

