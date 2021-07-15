---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-08-30T12:16:14Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/google-schema-markup-to-custom-menus-in-wordpress.jpg"
slug:  "how-to-add-google-schema-markup-to-custom-menus-in-wordpress"
tags:  ["Coding Tutorials"]
title:  "How To Add Google Schema Markup To Custom Menus In Wordpress"

---


<p>There is a lot written out there regarding <a href="http://schema.org/docs/gs.html" target="_blank" rel="noopener">proper use of Google Schema markup</a> in helping with SEO. Just do a search for JSON-LD (Google&#8217;s preferred method) and the tutorials abound.</p>
<p>So when a client asked that I add this markup specifically to their social links in the footer, it seemed a minor task that could be finished after a little light reading of the documentation.</p>
<p>Yet, looking at a few posts <a href="https://builtvisible.com/implementing-json-ld-wordpress/" target="_blank" rel="noopener">regarding JSON-LD</a>, I realized this client was not asking me to enter the markup this way (for the overall site), but instead wanted me to insert the microdata around and within each link of the custom menu.</p>
<p>So basically, this was not a once-for-all code to cover the whole site, but specifically adding Google Schema markup to custom menus in WordPress.</p>
<h3>How to add Google Schema markup to custom menus in WordPress.</h3>
<p>So let this be our social media example code (spaced out for readability):</p>
{{< highlight markdown "style=pygments" >}}<div class="menu-3-container">
  <ul id="menu-3" class="menu">
    
    <li id="menu-item-11103">
      <a target="_blank" href="https://www.facebook.com/travisdotmedia">Facebook</a>
    </li>
    
    <li id="menu-item-11104">
      <a target="_blank" href="https://www.linkedin.com/in/travisrodg">LinkedIn</a>
    </li>
    
    <li id="menu-item-11105">
      <a target="_blank" href="https://twitter.com/travisdotmedia">Twitter</a>
    </li>
    
    <li id="menu-item-11106">
      <a target="_blank" href="https://www.youtube.com/user/travisdotmedia">Youtube</a>
    </li>

  </ul>
</div>{{< / highlight >}}
<p>&nbsp;</p>
<p>And let&#8217;s say I want to add these three pieces of microdata to each social media link:</p>
{{< highlight markdown "style=pygments" >}}<span itemscope itemtype="http://schema.org/Organization">

<link itemprop="url" href="https://travis.media/">

<a itemprop="sameAs" href="https://facebook.com/travisdotmedia">FB</a>{{< / highlight >}}
<p>&nbsp;</p>
<p>At first glance, this could be achieved three different ways.</p>
<h3>1. wp_nav_menu() and a hook?</h3>
<p>First, I began with modifying the properties of the wp_nav_menu() function. I was able to achieve only one of the above requirements by adding the <span itemscope itemtype=&#8221;http://schema.org/Organization&#8221;> to the &#8216;before&#8217; and &#8216;after&#8217; properties. One only!</p>
<p>Second, I was then able to achieve the itemprop=&#8221;sameAs&#8221; in the link by hooking into the nav_menu_link_attributes and dropping this gem into functions.php.</p>
{{< highlight php "style=pygments" >}}function add_menu_atts( $atts, $item, $args ) {
  $atts['itemprop'] = 'sameAs';
  return $atts;
}
add_filter( 'nav_menu_link_attributes', 'add_menu_atts', 10, 3 );{{< / highlight >}}
<p>But that is only two of the three requirements.</p>
<p>How to get that <link> tag in there?? From what I can tell, we cannot do all three with the wp_nav_menu() properties alone.</p>
<h3>2. The Walker class?</h3>
<p>Second, I considered a Walker class and basically, I still don&#8217;t feel comfortable enough with Walker classes to go this route.</p>
<h3>3. jQuery!</h3>
<p>Finally, our buddy jQuery. And it was indeed jQuery to the rescue in the instance.</p>
<p>Let me tell you how it worked:</p>
<p>I created a new file in the js folder, lets call it social-schema.js.</p>
<p>First, I wrapped my code so that I could <a href="https://premium.wpmudev.org/blog/adding-jquery-scripts-wordpress/" target="_blank" rel="noopener">use the $ in WordPress instead of jQuery</a>:</p>
{{< highlight javascript "style=pygments" >}}(function($) {

  //Code goes here

})( jQuery );
{{< / highlight >}}
<p>Next, using .wrapInner, I wrapped each <li> of the menu with a <span> and the following schema markup.</p>
{{< highlight javascript "style=pygments" >}}(function($) {

  //wrap each <li> with a <span> and schema
  $( "#menu-3 li" ).wrapInner( '<span itemscope itemtype="http://schema.org/Organization"></span>' );

})( jQuery );



//creating this structure for each one
/*<li id="menu-item-11103">
  <span itemscope itemtype="http://schema.org/Organization">
      <a target="_blank" href="https://facebook.com/travis.media">Facebook</a>
  </span>
</li>*/{{< / highlight >}}
<p>&nbsp;</p>
<p>Then I used .prepend to drop the <link> text right after each <span></p>
{{< highlight javascript "style=pygments" >}}(function($) {

  //wrap each <li> with a <span> and schema
  $( "#menu-3 li" ).wrapInner( '<span itemscope itemtype="http://schema.org/Organization"></span>' );

  //add a <link> after each span for each <li>
  $( "#menu-3 li span" ).prepend( '<link itemprop="url" href="https://www.generalkinematics.com/">' );

})( jQuery );



//creating this structure for each one
/*<li id="menu-item-11103">
  <span itemscope itemtype="http://schema.org/Organization">
    <link itemprop="url" href="https://travis.media">
      <a target="_blank" href="https://facebook.com/travis.media">Facebook</a>
  </span>
</li>*/{{< / highlight >}}
<p>&nbsp;</p>
<p>Finally, I used .attr to attach the sameAs itemprop with each of the actual links.</p>
{{< highlight javascript "style=pygments" >}}(function($) {

  //wrap each <li> with a <span> and schema
  $( "#menu-3 li" ).wrapInner( '<span itemscope itemtype="http://schema.org/Organization"></span>' );

  //add a <link> after each span for each <li>
  $( "#menu-3 li span" ).prepend( '<link itemprop="url" href="https://www.generalkinematics.com/">' );

  //add itemprop to each link
  $( "#menu-3 li a").attr('itemprop', 'sameAs');

})( jQuery );



//creating this structure for each one
/*<li id="menu-item-11103">
  <span itemscope itemtype="http://schema.org/Organization">
    <link itemprop="url" href="https://travis.media">
      <a target="_blank" rel="me" href="https://facebook.com/travis.media" itemprop="sameAs">Facebook</a>
  </span>
</li>*/
{{< / highlight >}}
<p>&nbsp;</p>
<p>And Voila!</p>
<h3>But wait&#8230;</h3>
<p>Hold on&#8230;..the itemprop=&#8221;sameAs&#8221; is on the wrong side of the href! In the example given, it was supposed to come before! Well, I tried so hard to swap them to no avail. However, when I ran the code through Google&#8217;s <a href="https://search.google.com/structured-data/testing-tool" target="_blank" rel="noopener">Structured Data Testing Tool</a>, it passed with flying colors.</p>
<p>No worries.</p>
<p><strong><em>Have you found another, or better, way to add Google schema markup To custom menus In WordPress? I would love to hear it below!</em></strong></p>



