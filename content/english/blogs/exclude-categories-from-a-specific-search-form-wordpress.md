---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-01-08T15:28:45Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/exclude-categories-from-a-specific-search-form.jpg"
slug:  "exclude-categories-from-a-specific-search-form-wordpress"
tags:  ["Coding Tutorials"]
title:  "How To Exclude Categories From A Specific Search Form In WordPress"

---


<p>Excluding categories in WordPress is a fairly simple endeavor, whether it be in the loop or in the search query.</p>
<p>However there are times when you have multiple different search forms in WordPress and you may need to manipulate only one of them.</p>
<p>In this post we will look specifically at how to exclude categories from a specific search form in WordPress.</p>
<p>For example you have two forms. One searches for all post types (post, page, etc.) and the other only searches for posts. We want the one that searches for posts only to exclude a couple of categories.</p>
<h3>Video Tutorial</h3>

{{< youtube DVLmTwRXMD8 >}}

<h3>Written Tutorial</h3>
<p>If you prefer not to watch the video or need more instructions, then continue reading.</p>
<p>Here is the code to do it:</p>
{{< highlight php "style=pygments" >}}<?php

add_filter( 'pre_get_posts' , 'exclude_cats_blog_search' );
function exclude_cats_blog_search( $query ) {

    if ( $query->is_search &amp;&amp; $_GET['post_type'] == 'post') {
        $query->set( 'category__not_in' , array( 121, 203 ) ); //replace with your specific category IDs
}
{{< / highlight >}}
<p>If the query is search and the post type of our Get request form is a post, then exclude the categories in the array.</p>
<p>And that&#8217;s it. That is how you can exclude categories from a specific search form in WordPress</p>
<p>Hope this helps!</p>
<p>Cheers!</p>



