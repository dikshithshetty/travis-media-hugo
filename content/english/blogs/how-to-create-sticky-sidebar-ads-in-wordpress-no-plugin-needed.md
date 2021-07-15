---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2019-01-28T06:47:02Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/sticky-sidebar-ads-in-wordpress.jpg"
slug:  "how-to-create-sticky-sidebar-ads-in-wordpress-no-plugin-needed"
tags:  ["Coding Tutorials"]
title:  "How to Create Sticky Sidebar Ads in WordPress (No Plugin Needed)"

---

<div class="lead-paragraph"><span class="dropcap">S</span>ticky sidebar ads can be effective in WordPress, especially in long posts that leave much of the sidebar area empty. In this article, we&#8217;ll use a little JavaScript to create this functionality without the need for a plugin.</div><hr class="lead-hr">



<p>I went through a phase last year <a href="/balanced-solution-to-the-wordpress-sidebar-debate">where I ditched my sidebar</a>. I liked the minimalist look and the effort to keep the reader focused on the article at hand and not be distracted by things in the sidebar. </p>



<p>I still think of it as a great strategy, but I eventually missed the sidebar and the great things it offered, so I brought it back. </p>



<p>But one thing that never sat right with me was all the empty space in long articles. Once your sidebar runs out, the rest of the article is left with a gaping space on the side of the screen.</p>



<p>And this is where I think sticky sidebar ads can serve a great purpose. Here&#8217;s how it works:</p>



<p>Once the reader scrolls to the end of the sidebar, the last ad, or announcement, or whatever widget you put there, &#8220;sticks&#8221; to the side of the screen and scrolls on down the page with you. </p>



<p class="has-background has-very-light-gray-background-color">Want an example? View this post on Desktop or Table, scroll down the page,  and when you get to the last widget (currently an opt in for an ebook of mine) it will begin to scroll down the page with you. Then as you reach the bottom of the content it &#8220;releases&#8221; and pops back up the page to join the sidebar again.</p>



<p>I see a lot of people doing this with ads, but again, you can do this with anything.</p>



<h2>How to create a sticky sidebar ad in WordPress</h2>



<p>Here are the JavaScript ingredients:</p>



<h3>1. Grab the ID of your widget and of your Content</h3>



<p>In Chrome, right click on the element and click Inspect. This will open the Chrome Developer Tools. Find the section ID for your Element. I am using a Thrive Leads widget so mine would be <em>widget_thrive_leads-4</em>:</p>



<figure class="textcenter"><img src="/images/2019/12/sticky_sidebar_ads_section_id.jpg" alt="" class="wp-image-7175" /></figure>



<p>Do the same for your content area. There are usually two sections to your page: The content area, and the aside (sidebar). Grab the ID of the content area. In my case, it&#8217;s g<em>enesis-content.</em></p>



<figure class="textcenter"><img src="/images/2019/12/sticky-sidebar-ad-content-id.jpg" alt="" /></figure>



<h3>2. The code explained</h3>



<p>There are couple of varables that you want to attain:</p>



<ol><li>Distance from the top of the page to the sidebar ad.</li><li>The height of the entire content area.</li><li>The height of the entire sidebar</li><li>We&#8217;ll use $(window).scroll to measure how far we&#8217;ve scrolled from the top.</li></ol>



<p>Next, we only want this sticky sidebar ad to happen if the content is longer than the sidebar. And to be safe, we&#8217;ve added 1000px padding. </p>



<p>Next, if we&#8217;ve scrolled up to, or past, the distance to the sticky sidebar ad, we add the class &#8216;sticky-ad&#8217; which creates the &#8216;sticky&#8217; effect. Here&#8217;s the CSS for that:</p>



{{< highlight css "style=pygments" >}}.sticky-ad {
    position: fixed;
    top: 10px;
    max-width: 312px;
}{{< / highlight >}}



<p>Be sure to set the max-width to whatever the max width of your sidebar widgets are. </p>



<p>Finally, we need to &#8220;release&#8221; the ad back to the sidebar when we reach the bottom of the content. So if our scroll height from the top of the page exceeds the content height, we remove the &#8216;sticky-ad&#8217; class. I also put 1000 padding on this to be sure it releases a bit early. </p>



<h3>3. The code</h3>



<p>So with all that said, here&#8217;s the code. You can place this in your JavaScript file or if you only want this script to load on blog posts you can put it in functions.php with the logic of:</p>



{{< highlight php "style=pygments" >}}
if (is_single() &amp;&amp; !wp_is_mobile()){?>
  //JavaScript code goes here
<?php
}{{< / highlight >}}



<p>And here&#8217;s the full code (<strong>be sure to replace the widget and content variables with your own</strong>):</p>



{{< highlight javascript "style=pygments" >}}(function($) {

  // After page has loaded so elements fall into place
  $(window).on('load', function() {

    // Distance from top of page to sidebar ad in px
    var adFromTop = $('#widget_thrive_leads-4').offset().top

    // Height of entire content area
    var contentHeight = $('#genesis-content').height();

    // Height of entire sidebar
    var sidebarHeight = $('#genesis-sidebar-primary').height();

    // Making sure my content is longer than my sidebar with 1000px padding
    if (sidebarHeight < contentHeight + 1000) {

      $(window).scroll(function() {
        // If scroll distance from top exceeds by ad distance from top, add class
        if ($(window).scrollTop() >= adFromTop) {						 
          $('#widget_thrive_leads-4').addClass('sticky-ad');
        } else {
          $('#widget_thrive_leads-4').removeClass('sticky-ad');
        }

        // If scroll distance from top is greater than content height remove class. Added 1000px to pull ad out a bit before reaching the bottom.
        if ($(window).scrollTop() > contentHeight - 1000) {
          $('#widget_thrive_leads-4').removeClass('sticky-ad');
        }
      });    
    }
  });
})( jQuery );{{< / highlight >}}



<h3>Why jQuery?</h3>



<p>For this sort of thing, jQuery just works better. Yes I know the bloat of jQuery and 99% of the time will seek out a vanilla JS solution.</p>



<p>In this case, the heights with vanilla JS differed with different browsers causing the sticky sidebar ad to &#8220;stick&#8221; and &#8220;release&#8221; at bad times. jQuery was consistent in all, so I went with that. </p>



<p>If you prefer the vanilla JS solution for this, then here&#8217;s the code to do it, but be sure to test and tweak for different browsers. For instance, it just didn&#8217;t work well in Firefox. </p>



{{< highlight javascript "style=pygments" >}}document.addEventListener('DOMContentLoaded', function() {

  var sidebarAd = document.getElementById('#widget_thrive_leads-4');
  
  // When the user scrolls the page, execute the function below 
  window.onscroll = function() {adStick()};
 
  // Get the navbar
  var content = document.getElementById("genesis-content");
  var scrollTop = window.pageYOffset || (document.documentElement || 
  document.body.parentNode || document.body).scrollTop
 
  // Get the offset position of the ad widget
  var sticky = sidebarAd.offsetTop;
  var contentHeight = content.offsetHeight;
 
  // Add the sticky class to the navbar when you reach its scroll 
  position. Remove "sticky" when you leave the scroll position
  function adStick() {
    if (window.pageYOffset >= sticky - 40) {
      sidebarAd.classList.add("sticky-ad")
    } else {
      sidebarAd.classList.remove("sticky-ad");
    }
  
    if (window.pageYOffset > contentHeight - 1000) {
      sidebarAd.classList.remove("sticky-ad");
    } 
  }
}, false);{{< / highlight >}}



<h3>Conclusion</h3>



<p>And with a little bit of JavaScript we can add a sticky sidebar ad to our WordPress site without any plugin.</p>



<p>Let me know if you have any questions or want to contribute as to why the vanilla JS solution works differently in different browsers.</p>



