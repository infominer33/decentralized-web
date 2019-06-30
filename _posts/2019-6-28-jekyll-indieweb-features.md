---
layout: post
title: "Jekyll-Indieweb Features"
description: "Jekyll-Indieweb: Decentralized Web Histories"
tags:
 - indieweb
 - Jekyll
date: 2019-6-28
permalink: /indieweb/reboot/
published: false
---

Besides this site, I'm running two different Indieweb Static Site themes.

* [Static Sites for an Indieweb](https://web-work.tools/indieweb) - published using [AngeloStavrow/indigo](https://github.com/AngeloStavrow/indigo)

* [The Agoric Records](https://agoric-records.xyz) - published using [dumaurier/pwa_jekyll](https://github.com/dumaurier/pwa_jekyll)

I've not fully explored the indieweb features of any of these themes, but its a way to publish some content and learn about this cool technology and movement.

## New and Improved [miklb/jekyll-indieweb](https://github.com/miklb/jekyll-indieweb)


Sine the [last time](/indieweb/miklb-jekyll-deployed/) I deployed this website, things have changed, quite a bit!

![](https://i.imgur.com/ahnVZ9tl.png)

* [Jekyll Indieweb and Micropub](https://herestomwiththeweather.com/2017/11/27/jekyll-indieweb-and-micropub/) - Live example of V1 Jekyll indieweb.

I really liked the old design, I'm not gonna lie. However, I'm not complaining. This is fun!

What I really care about is the indieweb features, and I'm going to share here a systematic exploration of them.

My first attempt at learning to use indieweb tech, I tried following all of the guides, and put a bunch of stuff in an existing site, and failed at many of them :)

Now, I've started with themes built for indieweb, and am reverse-engineering them to better understand the technologies and how they are used.

## Relevant Specs Review

Reviewing from a similar post I did on Indigo, a Hugo Indieweb theme, I can see many of the indieweb elements are the same, so I'll grab some material from there, to review.


## h-card

```
h-card is a simple, open format for publishing people and organisations on the web. h-card is one of several open microformat draft standards suitable for embedding data in HTML.
```

* [microformats.org/wiki/h-card](http://microformats.org/wiki/h-card)

Yay! Structured Data! These are the bits that add flavor and context, for the machines we communicate through, to otherwise indistinguishable (to a machine) info.

> The class h-card is a root class name that indicates the presence of an h-card.
>
>For minimal examples where at most p-name, u-url and u-photo are required (such as the first given above), only the root class name is needed — see [implied properties](http://microformats.org/wiki/microformats-2-implied-properties).


Basically, it seems that the h-card is the root for the rest of the data-structure's we're reviewing.

If find one in the wild, an h-card will b nearby.

### h-card properties

So you can see, the idea is to give people and organizations a variety of ways to identify themselves.

h-card properties, inside an element with class h-card:

* p-name - The full/formatted name of the person or organization
* p-honorific-prefix - e.g. Mrs., Mr. or Dr.
* p-given-name - given (often first) name
* p-additional-name - other (e.g. middle) name
* p-family-name - family (often last) name
* p-sort-string - string to sort by
* p-honorific-suffix - e.g. Ph.D, Esq.
* p-nickname - nickname/alias/handle
* u-email - email address
* u-logo - a logo representing the person or organization (e.g. a face icon)
* u-photo - a photo of the person or organization
* u-url - home page or other URL representing the person or organization
* u-uid - universally unique identifier, preferably canonical URL
* p-category - category/tag
* p-adr - postal address, optionally embed an h-adr
* Main article: h-adr
* p-post-office-box - post office box description if any
* p-extended-address - apartment/suite/room name/number if any
* p-street-address - street number + name
* p-locality - city/town/village
* p-region - state/county/province
* p-postal-code - postal code, e.g. US ZIP
* p-country-name - country name
* p-label
* p-geo or u-geo, optionally embed an h-geo
* Main article: h-geo
* p-latitude - decimal latitude
* p-longitude - decimal longitude
* p-altitude - decimal altitude
* p-tel - telephone number
* p-note - additional notes
* dt-bday - birth date
* u-key - cryptographic public key e.g. SSH or GPG
* p-org - affiliated organization, optionally embed an h-card
* p-job-title - job title, previously 'title' in hCard, disambiguated.
* p-role - description of role
* u-impp per RFC4770, new in vCard4 (RFC 6350)
* p-sex - biological sex, new in vCard4 (RFC 6350)
* p-gender-identity - gender identity, new in vCard4 (RFC 6350)
* dt-anniversary



## Indieweb Features





I think the easiest way is to look at a complete html document and see how many microformats I can recognize.

Looking at the home-page, the first thing to jump out at me is 

I think the easiest way is to look at a complete html document and see how many microformats I can recognize.

Looking at the home-page, the first thing to jump out at me is 

The first indieweb markup I see is in our User Card.

I'm actually Infominer, not Kyle Den Hartog. However, he sponsored the creation of this resource, so I thought it would be nice to feature his info there for a while

```html
<div class="usercard-avatar">
  <img class="usercard-img u-photo" alt="Kyle Den Hartog" src="https://sourcecrypto.pub/decentralized-web/assets/images/kyle_dh.png">
</div>
<div class="usercard-body">
  <h2 class="title">Brought to you by <span class="p-name">Kyle Den Hartog</span></h2>
  <p class="subtitle"><a href='https://kyledenhartog.com/'>Kyle Den Hartog</a> wants to see a world where passwords are eliminated as the primary form of authentication. This vision led him to be an eager contributor to the design and development of DID-Auth along with other standards in the decentralized identity community. <br /><br/>As part of his commitment to the cause, he has <a href='https://web-work.tools/services/#iso-clients-who-want-bitcoin-related-content'>sponsored</a> some of the research required to create this resource.</p>
```

Here we see the `u-photo`, and `p-name`:

- p-name - The full/formatted name of the person or organization
- u-photo - a photo of the person or organization



```html
	<li class="profile">
	<a href="https://twitter.com/kyle_dh" class="twitter" title="Twitter" rel="me">

<!--snip-->

	<li class="profile">
	<a href="https://github.com/kdenhartog" class="github" title="GitHub" rel="me">

<!--snip-->
							
	<li class="profile">
	<a href="mailto:mail@kyledenhartog.com" class="email u-email" title="Email">

<!--snip-->

							
    <li class="profile"><a href="https://sourcecrypto.pub/decentralized-web/feed.xml" class="rss" title="RSS">
    
```							


```html
<article class="post h-entry">
	<header class="entry-header">
			
	<h1 class="title p-name">
		
		<a class="u-url" href="/decentralized-web/histories/">
			Decentralized Web Histories
		</a>
```		

```html  
    <header>
      <h2 class="p-name">
        
      </h2>
    </header>
  


  <div class="e-content">
```