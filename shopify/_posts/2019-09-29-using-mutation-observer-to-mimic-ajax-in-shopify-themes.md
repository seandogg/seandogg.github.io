---
layout: post
title: Using Javascript and MutationObserver for Boosting Buyer Incentives on Shopify with Free Shipping
description: >
   Using MutationObserver via JavaScript is helpful for watching Shopify's cart object in real time without a page refresh. Here's how I created a countdown to free shipping using the Web API.
image: /assets/img/blog/eye.jpg
excerpt_separator: <!--more-->
comments: true
---

[MutationObserver](https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver) is a super handy tool in the front-ender's toolbox -- especially when it comes to Shopify themes. This is how I used it with the [Streamline theme](https://archetypethemes.co/products/streamline) from Archetype -- but it can certainly be applied to a bunch of other themes too.
 
<!--more-->

![Today's Task](/assets/img/blog/shopify-free-shipping-countdown.png){:.lead data-width="800" data-height="100"}
The end goal for this task is creating a countdown for free shipping. 
{:.figure}

---

**Here's the business logic:** our customer spends $55, and her shipping is free. Our merchant needs a nice little message near the cart total showing the customer how much more they should spend to get free shipping. 

---
Archetype (arguably the top theme developers working with Shopify at the moment) has some nice [javascript event listeners](https://archetypethemes.co/blogs/streamline/javascript-events-for-developers) baked into their themes. We have one for **page load**, another for **cart updated**, and even a **product added to ajax cart** event. 

**The issue in this case was that none of these will work.** 

This is because Archetype returns a [Product Object](https://help.shopify.com/en/themes/liquid/objects/product) on the **product added to Ajax cart**. 

The **product object** won't help us... as it won't give us the total which comes from the **cart object**, and the **cart updated** event will only work when the customer actually changes the quantity of a cart item from the **cart page**. Bummer!

Luckily, in the DOM, we have the cart price being updated dynamically via AJAX without a page refresh. Nice! 

So, customer adds a product -- price updates, and we have something to work with -- a source of truth, if you will. 

Here's our markup:

{% highlight html %}
  <a href="{% raw %}{{ routes.cart_url }}{% endraw %}" id="StickyItems">{% raw %}{{ 'cart.general.item_count' | t: count: cart.item_count }}{% endraw %}</a> 
  
  <!-- this is updated via theme JS, and changes dynamically already -- no refresh needed -->
  <span id="StickySubtotal">{% raw %}{{ cart.total_price | money }}{% endraw %}</span> 
{% endhighlight %}

Our `MutationObserver` will watch the **StickySubtotal** span, and anytime it updates, we'll run some functions to create our countdown and update the DOM in real-time. First, let's add the markup to show the message:

{% highlight html %}
{% raw %}

    <!-- if the cart count is over 0 -->
    {% if cart.items.size > 0 %} 
    
        <!-- set the free shipping goal in Shopify's money format -->
        {% assign shipping_value = 5500 %} 
        
        <!-- output the shipping value to the DOM on page load and hide it -->
        <span id="shippingValue" style="display: none;">{{ shipping_value }}</span> 
        
        <!-- set the cart_total variable -->
        {% assign cart_total = cart.total_price %}
        
        <!-- Subtract the cart_total from the shipping value (this only happens on load!) -->
        {% assign shipping_value_left = shipping_value | minus: cart_total %}
        
        <!-- this is our free shipping msg that we'll update when they add an item -->
        <p class="shipping-savings-message">
       
        {% if shipping_value_left > 0 %}
          <span>{{ shipping_value_left | money }}</span> away from free shipping!
        {% else %}
          Awesome, you've got free shipping!
        {% endif %}
        
        </p>
          
    {% endif %}
    
{% endraw %}
{% endhighlight %}

Now that we've got all of that brewing in the DOM, (and working on refresh), we can add our MutationObserver and begin updating the countdown. 

{% highlight javascript %}
{% raw %}
<script>

  // on page load (specific to archetype themes!)
  document.addEventListener('page:loaded', function() {
   
    // build an observer for DOM mutations
    const MutationObserver = window.MutationObserver 
                          || window.WebKitMutationObserver 
                          || window.MozMutationObserver;

    // set the target to listen on
    const targetNode = document.getElementById('StickySubtotal'); // watch the sticky-cart's subtotal
    const shippingSavingsMessages = document.querySelectorAll('.shipping-savings-message');
 
    // set the observer's config
    const config = {
      attributes: true,
      childList: true,
      characterData: true,
      subtree: true,
    };

    // setup our mutation observer
    const observer = new MutationObserver(function(mutations) {
      
      // for each mutation
      mutations.forEach(function(mutation) {
        console.log('mutation =', mutation); // help us see whats being mutated in the console
        
        // grab the target's inner HTML and regex it to output it into Shopify's money format
        let targetNodeValue = targetNode.innerHTML;                               // the StickySubtotal's value / innerHTML
        const subtotalFromMoney = Number(targetNodeValue.replace(/[\$,.]/g, "")); // this takes $20.25 and regexes it to 2025
        const shippingValue = document.getElementById('shippingValue').innerHTML; // grabs the shipping value from the DOM
        
        // get the difference of the two values
        const priceDiff = shippingValue - subtotalFromMoney; // it's just math ok?
        const priceDiffToMoney = (priceDiff/ 100).toFixed(2).replace(/\d(?=(\d{3})+\.)/g, "$&,"); // this takes the difference and regexes it back into money! so 2025 would become 20.25
        
        // if the shipping value is more than the subtotal from money
        if (priceDiff > 0) {
         
          // for each case where the shippings-saved-message appears
          shippingSavingsMessages.forEach(function(shippingSavingsMessage) {
            // edit the DOM and update the value of the shipping message
            shippingSavingsMessage.innerHTML = '<span>$' + `${priceDiffToMoney}` + '</span> away from free shipping!'; 
          })
          
        // if it's not, let's tell them they've got free shipping.
        } else {
          shippingSavingsMessages.forEach(function(shippingSavingsMessage) {
            shippingSavingsMessage.innerHTML = "Awesome, you've got free shipping!";
          })
        }
      });
    });
    observer.observe(targetNode, config);
  });
  
</script>
{% endraw %}
{% endhighlight %}

And that's it! I'm sure there's other ways to achieve this, and I'd love to hear how you'd approach this problem. 

For now, we have a unique way to observe the cart object's subtotal and have created a handy little message that engages our customer and upsells to free shipping. 
