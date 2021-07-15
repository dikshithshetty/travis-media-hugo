---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2019-04-12T06:57:48Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/wordpress-transients-featured-image.jpg"
slug:  "wordpress-transients"
tags:  ["Coding Tutorials"]
title:  "What are WordPress Transients and How Can I Use Them?"

---


<p class="textcenter"><img src="/images/2019/12/wordpress-transients-featured-image.jpg" data-rjs="2" /></p>
<div class="lead-paragraph"><span class="dropcap">U</span>sing WordPress transients to cache data can help to speed up your site&#8217;s performance significantly. But how do we use them? Let&#8217;s discuss it in this post.</div><hr class="lead-hr">



<p>Before I <a href="https://www.youtube.com/watch?v=WLYyfWe60_I&amp;t=60s" target="_blank" rel="noreferrer noopener" aria-label="took the software job I'm currently at (opens in a new tab)">took the software job I&#8217;m currently at</a>, I underwent a number of interviews. In doing so, I had this question asked:</p>



<p>&#8220;If you had multiple queries being called on the homepage in WordPress, and it was causing a slow load time, how would you go about speeding this up?&#8221;</p>



<p>I really didn&#8217;t have a strong answer, so I said the magic words, &#8220;I don&#8217;t know what I would do, yet, without actually seeing the issue in person. What&#8217;s the answer?&#8221;</p>



<p>He replied, &#8220;Transients.&#8221;</p>



<p>Caching the queries with transients!</p>



<p>Okay. Honestly&#8230;..never heard of them. </p>



<p>So I went and learned all about WordPress transients.</p>



<h3>What are WordPress Transients?</h3>



<p>WordPress transients are simply a way to cache information temporarily in the database. There are three components: A key ( a string representing the name of the transient ), value ( the content you are storing in the cache ), expiration ( the lifespan of the transient ).</p>



<p>These are stored, for their lifespan, in the wp_options table.</p>



<p>There are three main functions involved:</p>



<ol><li><strong>set_transient()</strong>. To save a transient you use: <em>set_transient( $transient, $value, $expiration );</em>  $transient is a string representing the name of your transient. This can be anything, but choose a helpful name. $value is going to be a variable representing your data. $expiration will be the time before your transient expires. See below for helpful constants. </li><li><strong>get_transient()</strong>. To retrieve a transient you use: <em>get_transient( $transient ); </em></li><li><strong>delete_transient()</strong>. To delete a transient, you use <em>delete_transient( $transient ); </em></li></ol>



<p>And that&#8217;s it!</p>



<h3>Give me an example</h3>



<p>WordPress transients are really useful for resource-heavy database queries, and can significantly help to cut this number down. You can use the <a rel="noreferrer noopener" aria-label="Query Monitor plugin (opens in a new tab)" href="https://wordpress.org/plugins/query-monitor/" target="_blank">Query Monitor plugin</a> to see this number before and after the transient is set. </p>



<p>But here&#8217;s a simple example of how it can be used (note the comments):</p>



{{< highlight php "style=pygments" >}}// Check if the transient exists
$recipes = get_transient( 'my_recipes' );

// If the transient does not exist, then run the query and set the transient for the $recipes query. The next time this query is run, $recipes will exist as a transient and will not run a new query, but use the cached query instead.
if ( false === $recipes ) {
    $args = array(
        'post_type'   => 'recipe',
        'post_status' => 'publish'
    );

    $recipes = new WP_Query( $args );
    
    // Sets transient for one day duration
    set_transient( 'my_recipes', $recipes, DAY_IN_SECONDS );
}

// Note how only the query above is set as a transient. We want to cache the query. No need to cache the loop.
if( $recipes->have_posts() ) {
    echo '<ul>';
    while( $recipes->have_posts() ) {
        echo '<li><a href="' . get_permalink() . '">' . the_title( '', '', false ) . '</a></li>';
    }
    echo '</ul>';
}{{< / highlight >}}



<h3>Expiration Constants for WordPress Transients</h3>



<p>Here are some &#8220;WordPress native&#8221; constants that you can use for expiration times:</p>



{{< highlight php "style=pygments" >}}MINUTE_IN_SECONDS  = 60
HOUR_IN_SECONDS    = 60 * MINUTE_IN_SECONDS
DAY_IN_SECONDS     = 24 * HOUR_IN_SECONDS
WEEK_IN_SECONDS    = 7 * DAY_IN_SECONDS
MONTH_IN_SECONDS   = 30 * DAY_IN_SECONDS
YEAR_IN_SECONDS    = 365 * DAY_IN_SECONDS{{< / highlight >}}



<h3>An Important Note</h3>



<p><strong>Always have a fallback to the transient. </strong>The Codex states <em>&#8220;it is possible for the transient to not be available before the expiration time. Much like what is done with caching, your code should have a fallback method to re-generate the data should the transient not be available.&#8221; </em>This is why we check to see if it exists first. If for some reason it is not available, it will run the query again. No prob.</p>



<h3>Delete WordPress Transients When Saving/Updating/Deleting a Post</h3>



<p>When you make a change in a post that is using a transient, you want to see that change, right? Thus, you should delete the transient (it will set again) when making changes so those changes reflect. </p>



<p>WordPress has a few hooks we can use for this. Using our <em>my_recipe</em> transient example, we can delete when saving a post or deleting a post (and wherever else you&#8217;d want to use this).</p>



{{< highlight php "style=pygments" >}}function delete_my_recipes_transient() {
    delete_transient('my_recipes');
}
add_action( 'save_post', 'delete_my_recipes_transient'  );
add_action( 'delete_post', 'delete_my_recipes_transient'  );{{< / highlight >}}



<h3>Manage your transients</h3>



<p>There is also a nice plugin to see all the transients on your site and data about them (such as expiration, etc), called <a rel="noreferrer noopener" aria-label="Transients Manager (opens in a new tab)" href="https://wordpress.org/plugins/transients-manager/" target="_blank">Transients Manager</a>. Also, look at the <a href="https://wordpress.org/plugins/query-monitor/" target="_blank" rel="noreferrer noopener" aria-label="Query Monitor (opens in a new tab)">Query Monitor</a> plugin to monitor your performance pre and post-transients. </p>



<h3>Conclusion</h3>



<p>If you have multiple queries on a page or have some intensive queries that are causing performance issues for your site, then definitely look into implementing transients on your WordPress site. </p>



