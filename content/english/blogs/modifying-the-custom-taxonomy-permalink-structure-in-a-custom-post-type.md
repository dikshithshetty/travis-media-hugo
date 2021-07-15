---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-10-04T09:08:35Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/custom-taxonomy-permalink-structure-resize.jpg"
slug:  "modifying-the-custom-taxonomy-permalink-structure-in-a-custom-post-type"
tags:  ["Coding Tutorials"]
title:  "Modifying The Custom Taxonomy Permalink Structure In A Custom Post Type"

---


<div class="lead-paragraph"><span class="dropcap">L</span>et's say you create a custom post type named Online Bible. You visit your custom post type archive page and the URL is http://example.com/onlinebible. You create a post called Introduction and your URL is:</div><hr class="lead-hr">
<p>http://example.com/onlinebible/introduction.</p>
<p>Great!</p>
<p>Now you decide you want a custom taxonomy to categorize your posts by Books of this Bible, so you create a custom taxonomy called Books. So you create this taxonomy, add a Book category called Titus, create a new post called Summary and choose the Titus category for the post. You save your draft and look above the editor and see http://example.com/onlinebible/summary.</p>
<p>Wait. That&#8217;s not right. What you really wanted was:</p>
<p>http://example.com/onlinebible/titus/summary</p>
<p>I mean, you chose that category right? Shouldn&#8217;t it show up before &#8216;summary?&#8217;</p>
<h2>Your Custom Taxonomy Permalink Structure</h2>
<p>The answer is no. WordPress does not know to do this&#8230;&#8230;you actually have to tell it to. You have to instruct it as to your custom taxonomy permalink structure.</p>
<p>Let me show you now how to do it.</p>
<h3>Our Example</h3>
<p>So here is what we want:</p>
<p><em>Our main archive page: </em></p>
<p style="padding-left: 30px;">http://example.com/<strong>onlinebible</strong></p>
<p><em>Our categories when we choose them:</em></p>
<p style="padding-left: 30px;">http://example.com/onlinebible/<strong>titus</strong>/summary</p>
<p><em>No categories when none are chosen</em></p>
<p style="padding-left: 30px;">http://example.com/onlinebible/<strong>summary</strong></p>
<p>So let&#8217;s begin.</p>
<h3>1. Your Custom Post Type</h3>
<p>Here is our example custom post type called Online Bible:</p>
{{< highlight php "style=pygments" >}}//Setup Custom Post Type - Online Bible
add_action( 'init', 'create_custom_post_type_online_bible' );

function create_custom_post_type_online_bible() {
   $labels = array(
    'name' => __( 'Online Bible' ),
    'singular_name' => __( 'Online Bible' ),
    'all_items' => __('All Online Bible'),
    'add_new' => _x('Add new Online Bible', 'Online Bible'),
    'add_new_item' => __('Add new Online Bible'),
    'edit_item' => __('Edit Online Bible'),
    'new_item' => __('New Online Bible'),
    'view_item' => __('View Online Bible'),
    'search_items' => __('Search in Online Bible'),
    'not_found' =>  __('No Online Bible found'),
    'not_found_in_trash' => __('No Online Bible found in trash'),
    'parent_item_colon' => ''
    );

    $args = array(
    'labels' => $labels,
    'public' => true,
    'has_archive' => 'onlinebible',
	'query_var' => true,
    'menu_icon' => 'dashicons-book',
	'rewrite' => array('slug' => 'onlinebible/%books%'),
	'taxonomies' => array( 'post_tag', 'books'),
	'supports'  => array( 'title', 'editor', 'publicize', 'author', 'thumbnail' , 'custom-fields', 'excerpt', 'comments', 'genesis-cpt-archives-settings' )
	);

  register_post_type( 'online_bible', $args);
}{{< / highlight >}}
<p>In this custom post type we <em>want to make sure </em>that our rewrite argument has a slug of the custom post type and the dynamic category. We do this by making &#8216;onlinebible/%books% our slug.</p>
<h3>2. Our Custom Taxonomy</h3>
<p>The custom taxonomy (category) we want to create is Books, where we will add the books of our Online Bible.</p>
{{< highlight php "style=pygments" >}}function books_taxonomy() {  
    register_taxonomy('books', 'onlinebible', array(
		'labels' => array(
			'name'          => 'Books'
		,	'singular_name' => 'Book'
		,	'search_items'  => 'Search Books'
		,	'edit_item'     => 'Edit Book'
		,	'add_new_item'  => 'Add New Book'
		)
	,	'hierarchical' => true
	,	'query_var'    => true
	,	'rewrite'      => array('slug' => 'onlinebible', 'with_front' => false)
	)); // type taxonomy
}
add_action( 'init', 'books_taxonomy');{{< / highlight >}}
<p>In this custom taxonomy, we want our slug not to include this dynamic category, so we just put &#8216;onlinebible&#8217; as our slug.</p>
<h3>3. Our Dynamic Category Rewrite</h3>
<p>Now we have our custom post type archive page as http://example.com/onlinebible.</p>
<p>Check!</p>
<p>But when we go to create ANY post we get this URL:</p>
<p>http://example.com/onlinebible/%books%/postname</p>
<p>&#8230;and that will not work and will actually throw us an error (because of the %books% in the url).</p>
<p>We have to tell WordPress what we want it to do, and what we want it to do is find the chosen category term of the post and replace the %books% string in the URL with our chosen category term.</p>
<p>Here is how we do it:</p>
{{< highlight php "style=pygments" >}}function tm_books_post_link( $post_link, $id = 0 ){
    $post = get_post($id);  
        $terms = wp_get_object_terms( $post->ID, 'books' );
        if( $terms ){
            return str_replace( '%books%' , $terms[0]->slug , $post_link );
	} 
    return $post_link;  
}
add_filter( 'post_type_link', 'tm_books_post_link', 1, 3 );{{< / highlight >}}
<p>We get the chosen term of the post and replace %books% with that term slug.</p>
<p>Great!</p>
<p>Well, almost.</p>
<h3>The Problem</h3>
<p>What happens when there is no term chosen. What if we don&#8217;t want to choose a term and have the onlinebible/postname permalink structure instead?</p>
<p>We get an error. Why? Because if we do NOT choose a term, we get the http://example.com/onlinebible/%books%/postname URL (which throws us an error), mainly because <strong>our rewrite only happens when there is a term chosen</strong>.</p>
<p>Thus we need to add in a condition that removes the %book% in the URL if a term is not chosen.</p>
<p>We can do it by adding an else clause to replace our %books% with a blank space:</p>
{{< highlight php "style=pygments" >}}function tm_books_post_link( $post_link, $id = 0 ){
    $post = get_post($id);  
        $terms = wp_get_object_terms( $post->ID, 'books' );
        if( $terms ){
            return str_replace( '%books%' , $terms[0]->slug , $post_link );
	} else {
	    return str_replace( '%books%/' , '' , $post_link );
}
	
    return $post_link;  
}
add_filter( 'post_type_link', 'tm_books_post_link', 1, 3 );{{< / highlight >}}
<p><em>**And remember to put the &#8216;/&#8217; after &#8216;%books%&#8217; so that it will remove the extra one.</em></p>
<h3>Conclusion</h3>
<p>There are many other options to this and you can find a plethora of answers on <a href="https://wordpress.stackexchange.com" target="_blank" rel="noopener">https://wordpress.stackexchange.com</a> and search results on Google.</p>
<p>But I hope this helps in regards to the use of custom taxonomies acting as categories to your custom post type and nailing down the custom taxonomy permalink structure that you desire.</p>
<p><strong><em>How have you handled the custom taxonomy permalink structure in the past? What options have you given? Let me know below an as always, feel free to ask questions about the post.</em></strong></p>

Let's say you create a custom post type named Online Bible. You visit your custom post type archive page and the URL is http://example.com/onlinebible. You create a post called Introduction and your URL is:

---



