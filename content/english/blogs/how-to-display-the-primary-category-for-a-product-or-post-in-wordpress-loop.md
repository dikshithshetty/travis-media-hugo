---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-12-30T11:51:51Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/display-the-primary-category-for-a-product.jpg"
slug:  "how-to-display-the-primary-category-for-a-product-or-post-in-wordpress-loop"
tags:  ["Coding Tutorials"]
title:  "How to Display the Primary Category for a Product or Post In WordPress Loop"

---


<p>There will come a time where you will want to display the Primary Category for a Product or Post in a WordPress loop and <strong>only</strong> the Primary Category.</p>
<p>For example, a search results page and you want the entry meta of the results to display only the primary category.</p>
<p>First off, this is a Yoast construct, the idea of making a category a Primary Category, so we should keep that in mind when looking to display the Primary Category for a Product or Post.</p>
<p>So in this post, I want to show you how to do this and not only how to populate the Primary Category, but place it as a link in your entry meta.</p>
<h2>Getting The Primary Category from a WooCommerce product</h2>
<p><strong>WooCommerce Products:</strong></p>
<p>So in your WordPress loop you want to display <em>WooCommerce Products</em> with only the Primary Product Category displayed. And to add to that, you want that Category to be linked. Something like this:</p>
<p>&nbsp;</p>
<figure class="textcenter"><img src="/images/2019/12/display-the-primary-category-for-a-product-2.png" /><figcaption id="caption-attachment-3098" class="wp-caption-text">The item name is Flashlight and the Primary Category is Tools (a link).</figcaption></figure>
<p>&nbsp;</p>
<p>Well, here&#8217;s the code to pull that Primary Category and populate it as a link. Place it inside your loop:</p>
{{< highlight php "style=pygments" >}}<?php

//Grabs the Primary Category of the Product
$primary_term_product_id = yoast_get_primary_term_id('product_cat');
$postProductTerm = get_term( $primary_term_product_id );

//If the post type is a product, display the Primary Category Link
if ( 'product' === get_post_type() ) { ?>
  <div class="">
  <?php 
    if ( $postProductTerm &amp;&amp; ! is_wp_error( $postProductTerm ) ) {       
      echo '<a href="' .  esc_url( get_term_link( $postProductTerm->term_id ) ) . $postProductTerm->slug . '">';
      echo $postProductTerm->name;
      echo '</a>';
      }
   ?>
   </div><?php
}{{< / highlight >}}
<h2>Getting The Primary Category from a Post</h2>
<p><strong>Posts:</strong></p>
<p>And let&#8217;s say you want to display only the Primary Category of a <em>post</em>, perhaps after the date. And to add to that, you want that Category to be linked. Something like this:</p>
<p class="textcenter"><img src="/images/2019/12/display-the-primary-category-for-a-product-1.png" /></p>
<p>&nbsp;</p>
<p>Well, here&#8217;s the code to pull that Primary Category and populate it as a link. Place it inside your loop:</p>
{{< highlight php "style=pygments" >}}<?php

//Grabs the Primary Category of the Post
$primary_term_id = yoast_get_primary_term_id('category');
$postTerm = get_term( $primary_term_id );

//If the post type is a post, display the Primary Category Link
if( 'post' === get_post_type() ) { ?>
  <div class=""><?php the_time('m/j/Y'); ?> | <?php
    if ( $postTerm &amp;&amp; ! is_wp_error( $postTerm ) ) {  
      echo '<a href="' .  esc_url( get_term_link( $postTerm->term_id ) ) . $postTerm->slug . '">';
      echo $postTerm->name;
      echo '</a>';
    }
  ?>
  </div> <?php 
}{{< / highlight >}}
<p>&nbsp;</p>
<h3>One Caveat&#8230;</h3>
<p>Remember, your posts or products prior to Yoast implementing this feature in 2016 will not have a primary category so this will not work for those. In fact, it will leave a big, fat, blank space.</p>
<p>So you will need to return the category as normal.</p>
<p>Lets say there is no primary category and instead of returning them all you just want to return the first one. Well, you could put in an else to your if statement, targeting the first category in the array:</p>
{{< highlight php "style=pygments" >}}<?php
$postCategory = get_the_category();

else {
    echo '<a href="' .  esc_url( get_term_link( $postCategory[0]->term_id ) ) . $postCategory[0]->slug . '">';
    echo $postCategory[0]->name;
    echo '</a>';
  }{{< / highlight >}}
<p>Or let&#8217;s say you want to do the same with the product category:</p>
{{< highlight php "style=pygments" >}}<?php

$productTerms = get_the_terms( $post->ID, 'product_cat' );

else {
    if ( $productTerms &amp;&amp; ! is_wp_error( $productTerms ) ) {
      foreach ($productTerms as $productTerm) {
        if ($productTerm === reset($productTerms)) {
          echo '<a href="' .  esc_url( get_term_link( $productTerm->term_id ) ) . $productTerm->slug . '">';
          echo $productTerm->name;
          echo '</a>';
          }
        }
      }
    }{{< / highlight >}}
<p>&nbsp;</p>
<p>And that&#8217;s it! Let me know if you have any questions!</p>
<p>&nbsp;</p>



