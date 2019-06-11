---
layout: post
title: "Webmentions - Look Ma, No Hands!"
description: "A try at Using Webmentions."
date: "2019-05-21"
tags: indieweb github-pages resources github jekyll static-sites
subtitle: "A first attempt at using webmentions."
permalink: webmentions/
category: indieweb
---


## Edit-Test


<div class="h-card">
	<img src="https://infominer.id/indieweb/info.png" class="u-photo" width="40">
	<a href="https://infominer.id" class="u-url p-name">InfoMine ⧉</a>
</div>	


<div class="h-entry">
  <ul><li><a class="u-in-reply-to" href="https://aaronparecki.com/2018/12/15/14/indieweb">@aaronpk/your-first-webmention</a></li></ul>

  <p class="e-content">Thanks for this cool instructional!<br/><br/>Checkout <a href="https://infominer.id/indieweb/github/">indieweb/github</a> for an Awesome Collection of Indieweb GitHub Repositories.</p>

  <a href="https://infominer.id/indieweb/webmentions/" class="u-url">
  <time class="dt-published" datetime="2019-05-21">May 05, 2019</time></a>
</div>

<a href="https://brid.gy/publish/twitter"></a>

We'll test this, also:

```
<a href="https://brid.gy/publish/twitter"></a>
```
 

## Welcome!

The short version of how I got here:

Create a (free) GitHub personal access token:

![](https://imgur.com/IuHdqcCl.png)

It needs the `repo` scope.

![](https://imgur.com/b4G9F1rl.png)

Once I got my access token, I forked:

* [bmann/webpage-webmentions](https://github.com/bmann/webpage-webmentions) - Turnkey to heroku rendition of [voxpelli/webpage-webmentions](https://github.com/voxpelli/webpage-webmentions) (also Free)

![](https://imgur.com/5Tze7dC.png)

Click Deploy to heroku:

it's pretty straightforward... just make sure to format the address like so:

* [infomicro.herokuapp.com/](https://infomicro.herokuapp.com/)

Also free, and if you don't feel like doing this part, the first 10 people who try to can sign up through my endpoint at above address.

## Now What?

well, I followed a few other steps. 

First, I added all this to the head:


```

	<link href="https://micro.blog/infominer" rel="me" />
    <link rel="token_endpoint" href="https://tokens.indieauth.com/token">
	<link rel="authorization_endpoint" href="https://indieauth.com/auth">
    <link rel="micropub" href="https://infomicro.herokuapp.com/api/webmention" />
	<link href="https://instagram.com/infominer33" rel="me">
	<link href="https://infominer.id" rel="me"/>
	<link rel="webmention" href="https://webmention.herokuapp.com/api/webmention" />
	<link href="https://twitter.com/infominer33" rel="me">
	<link href="https://github.com/infominer33" rel="me">
	<link href="mailto:infominer@protonmail.com" rel="me">	
	<link href="https://keybase.io/infominer" rel="me">
    <link rel="pgpkey" href="https://infominer.id/indieweb/key.pub">
	<link href="https://infomicro.herokuapp.com/" rel="me"/>

```

As you can see, I signed up w:

* [micro.blog](https://micro.blog), and am self-hosted, so that's free.
* [indieauth.com](https://indieauth.com) (also free)
* [ownyourgram.com](https://ownyourgram.com/) - Even if you don't plan to use insta, go thru the steps here will help, if you are stuck.

## The Fun Stuff

<script id="webmention-hosted">
(function () {
var sn = document.createElement("script"), s = document.getElementsByTagName("script")[0], url;
url = document.querySelectorAll ? document.querySelectorAll("link[rel~=canonical]") : false;
url = url && url[0] ? url[0].href : false;
sn.type = "text/javascript"; sn.async = true;
sn.src = "//webmention.herokuapp.com/api/embed?url=" + encodeURIComponent(url || window.location);
s.parentNode.insertBefore(sn, s);
}());
</script>

