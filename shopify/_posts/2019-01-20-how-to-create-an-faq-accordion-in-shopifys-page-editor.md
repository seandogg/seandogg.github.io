---
layout: post
title: Creating An Accordion for Shopify Pages 
description: >
   In web development, an `accordion` is something that expands on a user's click.
image: /assets/img/blog/accordion.gif
excerpt_separator: <!--more-->
comments: true
---

<!-- Begin Accordion Snippet -->
<style>
  .so-tab {
    position: relative;
    width: 100%;
    overflow: hidden;
    margin: 25px 0;
  }
  .so-tab label {
    position: relative;
    display: block;
    padding: 0 25px 0 0;
    margin-bottom: 15px;
    line-height: normal;
    cursor: pointer;
  }
  .so-tab input {
    position: absolute;
    opacity: 0;
    z-index: -1;
  }
  .so-tab-content {
    max-height: 0;
    overflow: hidden;
    transition: max-height .35s;
  }
  /* :checked */
  .so-tab input:checked ~ .so-tab-content {
    max-height: none;
  }
  /* Icon */
  .so-tab label::after {
    position: absolute;
    right: 0;
    top: 0;
    display: block;
    -webkit-transition: all .35s;
    -o-transition: all .35s;
    transition: all .35s;
  }
  .so-tab input[type=checkbox] + label::after {
    content: "+";
  }
  .so-tab input[type=radio] + label::after {
    content: "\25BC";
  }
  .so-tab input[type=checkbox]:checked + label::after {
    transform: rotate(315deg);
  }
  .so-tab input[type=radio]:checked + label::after {
    transform: rotateX(180deg);
  }
</style>


<div class="so-accordion-wrapper">
  <div class="so-tab">
    <input id="so-tab-1" type="checkbox" name="tabs" />
    <label for="so-tab-1"><u>Click Me. I'm an accordion.</u></label>
    <div class="so-tab-content">
      <blockquote>
        <p>Well hello there buddy... click on that there title one more time and fold this thing back up! Otherwise, here's a bunch more text that would go on and on til the break of dawn.</p>
        <p>Here we are, reading placeholder, holding hands, together. Forever. And ever. And ever. And ever.</p>
        </blockquote>
    </div>
  </div>
</div>
<!--more-->

<br/>

**Note:** The following code snippet is **pure html/css** and does not require javascript or jquery. It should inherit your theme's style.

## Step 1: Copy/Paste [this code](#source-code) into Shopify
![Full-width image](/assets/img/blog/step1.jpg)

## Step 2: Save the page. View the frontend.

## Step 3: Change The Content
![Full-width image](/assets/img/blog/step2.jpg)

---

<div style="position: relative; padding-bottom: 62.5%; height: 0;"><iframe src="https://www.loom.com/embed/f52d3de3ef9b4635b6766b3a8a244cfc?autoplay=1" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;margin-bottom:25px;"></iframe></div>
## Source Code
<script src="https://gist.github.com/seandogg/ed55076b8913235bda1aa79f34cffe90.js"></script>

