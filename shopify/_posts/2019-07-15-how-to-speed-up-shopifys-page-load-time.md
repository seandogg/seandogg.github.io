---
layout: post
title: Improving Your Shopify Store's Page Load Time
description: >
   Your Shopify store is running slow. The most likely culprit? **Third-party Apps**
image: /assets/img/blog/slow.jpg
excerpt_separator: <!--more-->
comments: true
redirect_from: /how-to-speed-up-shopifys-page-load-time
---

We see it all too often... a merchant decides to run their domain through an online page speed test and, shocked with the results, immediately assumes their entire business is burning to the ground.
<!--more-->

Merchants with employees immediately divert underlings to solving the page load issues while the self-employed store owners frantically search for answers.

Those with little understanding of theme code begin **scouring the Shopify App Store**, reaching for anything that cools the flames of what is becoming a burning itch to have a faster Shopify store. 

Third-party Apps peddling so-called "speed boosts" are hastily installed, and then, minutes later the same apps are un-installed after they've only shaved off a dismal millisecond (but not before they've re-written most of your `assets` folder into un-maintainable code). 

## Step 1: Don't Trip

Before you call all-hands-on-deck, or imbibe in your own personal meltdown, there's a bit more to understand about Shopify, page speeds, and what it all means for the long game.

[GTMatrix](https://gtmetrix.com/), [Google PageSpeedTest](https://developers.google.com/speed/pagespeed/insights/) or [Pingdom](https://tools.pingdom.com/) each offer some popular tests. Try one out!

Psychologically, for merchants, running a site through these tests appeals to that **inner gamer/social media addict** in all of us. 

Suddenly, all we care about is raising that grade. After all, business depends on it... right?

## Let's compare some notable online stores

![Kylie's Score](/assets/img/blog/kyli.jpg){:.lead data-width="800" data-height="100"}
The fastest scaling ecommerce business in history isn't passing any speed tests.
{:.figure}

Take a deep breath, this might shock you... **[Apple.com](https://apple.com) regularly scores an F** (today it's a **C-**), **[Shopify's homepage](https://shopify.com) is scoring a D**, and the largest brands on Shopify ([**Kylie Cosmetics**](https://www.kyliecosmetics.com/) and [**FashionNova**](https://fashionnova.com)) are both **scoring an E** (worse than an F).

## Important Takeaway
These are some of the highest selling, most trafficked websites in online retail and they're basically bombing the page speed test. Yet, they're seeing **millions of orders** per year.

Am I saying it doesn't matter? **No!** `Time to first paint` is a noble and meaningful pursuit, one worthy of your time! It even reduces your carbon footprint.
‍
# What's actually slowing down your Shopify store?
## 1. Apps
Shopify -- bless their Canadian hearts -- are in the business of helping you sell. You pay them a monthly fee, they charge transaction fees, and they also earn revenue on Apps that you install from the Shopify App Store. 

Shopify has good reason to push apps to merchants. They solve complex business problems, extend the platform, and generally keep the party going.

Every time you install an app, it should be absolutely critical that you NEED that app. For each app installed, you're taking a performance hit -- and that page load score? These apps are **not** helping.

> Installing and uninstalling apps can have unintended ramifications and continue slowing down your site even after apps are uninstalled.
{:.lead}

For more reading, [checkout this amazing case study](https://medium.com/vitals/shopify-page-speed-3a104b330624).
‍
## 2. Carousels & Sliders
Pre-built themes almost always include a big juicy image slider or carousel. 

Often these sliders can be slow and dependent on external libraries which can dramatically delay page load time. 

Do we need these carousels in 2019? Probably not. Can we better utilize **the most important shopping display for your storefront**? Absolutely. 

>
Consider the segmentation and personalization possibilities on that slider's real estate. What if, based on customer tags, you swapped that bloated, resource-eating slider for a single custom image? 

With Liquid and some HTML/CSS it's possible to do this without a bulky app, and could be based on the customer's buying history or site visits. (I'll save the tutorial for another article).

## 3. Resource Requests
This one ties into #1. Apps make a ton of network requests and ideally your theme should have one CSS file and one JavaScript file (when compiled). 

>
Apps typically add multiple JS and CSS files, and sometimes make multiple "handshakes" with even more libraries and scripts, compiling resource requests even more.

This is when having a developer is vital for analyzing your theme's network requests. If you don't work with one already, [get in touch](mailto:hello@sean-orfila.com).
‍
## 4. Oversized Images
This is the low-hanging fruit. Big images will slow your roll and dramatically increase your page size and page load speed. A good goal is to keep each image under 50kb (max ~ 70kb for large images). 

Shopify utilizes a CDN (content delivery network), and they do some basic image optimization, but you've really got to be mindful not to upload non-optimized images if you're looking to run a fast website.

Try using something like [ImageOptim](https://imageoptim.com/mac) or [TinyJPG](https://tinyjpg.com) to help compress your images.   

## 5. Your Store-bought Theme
Most themes were built on JQuery and pre-built themes usually include a "kitchen sink" type of codebase to satisfy the vast amount of merchants that want vastly different features. 

With a custom theme, you can [use something like Slater](https://github.com/the-couch/slater-theme) that uses the latest ES6 code and things like [operator](https://github.com/estrattonbailey/operator) to help your theme run blazing fast.

With that speed comes some custom features specific to your business. A design based on detailed UX research and your store's analytics is a powerful way to find some positive ROI.

## Conclusions
The most important thing is to take the page speed test with a grain of salt (and don't freak out). Secondly, take a long hard look at that list of installed apps. Get rid of **everything** that isn't vital to your business, and seek help if you need an audit. [My inbox is open](mailto:hello@sean-orfila.com), or drop a comment below! 