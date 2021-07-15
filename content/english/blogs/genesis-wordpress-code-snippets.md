---
author: "Travis Rodgers"
date:  2018-08-08T10:19:26Z
description:  ""
draft:  false
slug:  "genesis-wordpress-code-snippets"
title:  "Genesis WordPress Code Snippets"

---


<p>This is a page for WordPress Code Snippets, but specifically for the Genesis Framework. As I come across helpful Genesis WordPress code snippets or create new code, I will share here in hopes to benefit other WordPress users out there:</p>
<div id="genesis-table-of-contents">
<h5><span style="text-decoration: underline;">Table of Contents</span></h5>
<p><a href="#custom-favicon">Add a Custom Favicon</a><br />
<a href="#read-more-link">Add a Read More Link to post excerpt</a><br />
<a href="#featured-image-custom">Display Featured Image &amp; Custom Size</a><br />
<a href="#insert-content-before-jetpack">Insert Content Before Jetpack Social Sharing and Related Posts</a><br />
<a href="#change-default-search-text">Change Default Search Text</a></p>
</div>
<h3 id="featured-image-custom">Display Featured Image &amp; Custom Size</h3>

{{< highlight php "style=pygments" >}}
// Register a custom image size for Singular Featured images

//Choose custom image size and remember to Regenerate Thumbnails
add_image_size( 'singular-featured-thumb', 768, 450, true ); 

//Hook to add image before entry content
add_action( 'genesis_before_entry_content', 'tm_display_featured_image' );

//Function to display image
function tm_display_featured_image() {
    if ( ! is_singular( array( 'post', 'page' ) ) ) {
        return; //ends function if not singular post or page
    }
    if ( ! has_post_thumbnail() ) {
        return; //ends function if no thumbnail chosen
    }
    // Display featured image above content
    echo '<div class="singular-featured-image">';
        genesis_image( array( 'size' => 'singular-featured-thumb' ) );
    echo '</div>';
}
{{< / highlight >}}

<p><a href="#genesis-table-of-contents">Back to top</a></p>
<hr />
<h3 id="read-more-link">Add a Read More link to Post Excerpt</h3>
{{< highlight php "style=pygments" >}}
// Add Read More Link to Excerpts
add_filter('excerpt_more', 'get_read_more_link');
add_filter( 'the_content_more_link', 'get_read_more_link' );
function get_read_more_link() {
   return '...&amp;nbsp;<a href="' . get_permalink() . '">[Read&amp;nbsp;More]</a>';
}
{{< / highlight >}}
<p><a href="#genesis-table-of-contents">Back to top</a></p>
<hr />
<h3 id="custom-favicon">Add a Custom Favicon</h3>
{{< highlight php "style=pygments" >}}
/** Adding custom Favicon */
add_filter( 'genesis_pre_load_favicon', 'custom_favicon' );
function custom_favicon( $favicon_url ) {
    return 'http://example.com/wp-content/uploads/favicon.png';
}
{{< / highlight >}}

<p><a href="#genesis-table-of-contents">Back to top</a></p>
<hr />
<h3 id="insert-content-before-jetpack">Insert Content Before Jetpack Social Sharing and Related Posts</h3>
{{< highlight php "style=pygments" >}}
<h3>Insert Content Before Jetpack Social Sharing and Related Posts</h3>
{{< highlight php "style=pygments" >}}
//Remove original Jetpack Social Sharing location
add_action( 'init', 'custom_init', 11 );
function custom_init() {
    //* if sharing_display() function does not exist, return
    if( ! function_exists( 'sharing_display' ) ) {
        return;
    }
    //* remove the callback sharing_display() for the 'the_content' filter.
    remove_filter( 'the_content', 'sharing_display', 19 );
}

// Remove JetPack Related Posts
function jetpackme_remove_rp() {
    if ( class_exists( 'Jetpack_RelatedPosts' ) ) {
        $jprp = Jetpack_RelatedPosts::init();
        $callback = array( $jprp, 'filter_add_target_to_dom' );
        remove_filter( 'the_content', $callback, 40 );
    }
}
add_filter( 'wp', 'jetpackme_remove_rp', 20 );

//Putting Jetpack Social Sharing after the content
add_action( 'genesis_after_entry_content', 'reposition_jetpack', 5 );
function reposition_jetpack() {
    if ( is_singular( 'post' ) &amp;amp;&amp;amp; function_exists( 'sharing_display' ) ) {
        sharing_display( '', true );
    }
}

//Putting JetPack Related Posts after the content
function wpb_jp_posts() {
    echo do_shortcode(' [jetpack-related-posts] ');
}
add_action( 'genesis_after_entry_content', 'wpb_jp_posts', 10 );

/* Now insert New Hook Before Social Sharing by using the 
'genesis_after_entry_content' but a priority number lower than 5 
(as social sharing was 5 and related posts was 10). */

{{< / highlight >}}
<p><a href="#genesis-table-of-contents">Back to top</a></p>
<h3 id="change-default-search-text">Change Default Search Text</h3>
{{< highlight php "style=pygments" >}}
//Change default search text
function themeprefix_search_button_text( $text ) {
	return ( 'Custom search phrase...');
	}

add_filter( 'genesis_search_text', 'themeprefix_search_button_text' );

{{< / highlight >}}

<p><a href="#genesis-table-of-contents">Back to top</a></p>



