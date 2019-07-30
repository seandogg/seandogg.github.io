---
layout: post
title: Improving Your Shopify Store's Page Load Time
description: >
   Your Shopify store is running slow. The most likely cause? **Third-party Apps**.
image: /assets/img/blog/slow.jpg
excerpt_separator: <!--more-->
comments: true
redirect_from: /how-to-speed-up-shopifys-page-load-time
---

I see it all too often. A Shopify merchant will run their domain through one of the many page speed tests and, seeing the results, immediately assume their entire business is on fire.
<!--more-->
 
Suddenly, employees are being diverted from important daily tasks to solve the dilema of slow page loads. Third-party apps peddling so-called "speed boosts" are hastily installed, and then tragicly un-installed (but not before they've re-written most of your `assets` folder). 

## Don't freak out

Before you call all-hands-on-deck, or have your own personal meltdown, there's a bit more to understand about Shopify, page speeds, and what it all means.

[GTMatrix](https://gtmetrix.com/), [Google PageSpeedTest](https://developers.google.com/speed/pagespeed/insights/) or [Pingdom](https://tools.pingdom.com/) each offer some popular tests.

Psychologically, for merchants, running a site through these tests appeals to that **inner gamer/social media addict**. Suddenly, all we care about is lowering that number. After all, business depends on it, right?

## Let's compare some notable online stores

![Kylie's Score](/assets/img/blog/kyli.jpg){:.lead data-width="800" data-height="100"}
The fastest scaling business in internet history isn't passing that speed test either.
{:.figure}

Take a deep breath. This might shock you... **[Apple.com](https://apple.com) regularly scores an F** (today it's a **C-**), **[Shopify's homepage](https://shopify.com) is scoring a D**, and the largest brands on Shopify ([**Kylie Cosmetics**](https://www.kyliecosmetics.com/) and [**FashionNova**](https://fashionnova.com)) are both **scoring an E** (worse than an F).

## Takeaway
These are some of the highest-volume, most-visited websites in online retail and they're bombing the page speed test. Yet they're seeing millions of orders a year.

Am I saying it doesn't matter? **No!** `Time to first paint` is a noble pursuit, and worthy of your time.

**Bottom line: don't beat yourself up over a low score.** We can all do better! And with data centers expected to consume 33% of global electricity by 2025, optimizing your store means you're doing your part in striving for lean code that **reduces your carbon footprint**. 
‍
# So... what's actually slowing down your Shopify store?
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

Do we need these carousels in 2019? Probably not. Can we better utilize the most important shopping display for your storefront? Absolutely.

Think about the segmentation and personalization possibilities. What if, based on customer tags, you personalized that slider based on each customer?

Consider swapping out any beefy sliders that aren't converting. 
‍
## 3. Resource Requests
This one ties into #1. Apps make a ton of network requests and ideally your theme should have one CSS file and one JavaScript file (when compiled). Apps usually add multiple JS and CSS files.

This is when having a developer is vital for analyzing your theme's network requests. If you don't work with one already, [get in touch](mailto:hello@sean-orfila.com).
‍
## 4. Oversized Images
This is the low-hanging fruit. Big images will slow your roll and dramatically increase your page size and page load speed. A good goal is to keep each image under 50kb (max ~ 70kb for large images). 

Shopify utilizes a CDN (content delivery network), and they do some basic image optimization, but you've really got to be mindful not to upload non-optimized images if you're looking for a fast site. 

## 5. Your Store-bought Theme
Most themes were built on JQuery and pre-built themes must include a "kitchen sink" type of codebase to satisfy a vast amount of people that want different features. 

With a custom theme, you can [use something like Slater](https://github.com/the-couch/slater-theme) that uses the latest ES6 code and things like [operator](https://github.com/estrattonbailey/operator) to help your theme run blazing fast.