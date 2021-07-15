---
author: "Travis Rodgers"
categories: ["Digital Strategy"]
date:  2018-08-25T14:57:35Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/change-the-open-graph-image-size.jpg"
slug:  "how-to-change-the-open-graph-image-size-in-yoast"
tags:  ["Digital Strategy"]
title:  "How To Change The Open Graph Image Size In Yoast"

---

<p>Here&#8217;s a quick article on how to change the size of your Open Graph image, or og:image, used by Yoast with just a little snippet of code.</p>
<p>I recently had a client ask for help in fixing this dilemma. Their website&#8217;s open graph image was strangely at a resolution of 1172 x 256 and as you can expect when shared on Facebook it create a bad crop.</p>
<p>I didn&#8217;t take much time to look into the &#8220;why&#8221; of the specific image size but instead told it use a certain, pre-defined, image size in WordPress, which is what the client wanted. In this specific example we chose it to be the <a href="https://codex.wordpress.org/Post_Thumbnails" target="_blank" rel="noopener">Large</a> size image.</p>
<p>This can be altered by placing the following filter into your functions.php. Just add it to the bottom:</p>
{{< highlight php "style=pygments" >}}function set_custom_facebook_image_size( $img_size ) {
    return 'large';
}
add_filter( 'wpseo_opengraph_image_size', 'set_custom_facebook_image_size' );{{< / highlight >}}
<p>Change &#8216;large&#8217; to any of the other <a href="https://codex.wordpress.org/Post_Thumbnails" target="_blank" rel="noopener">native WordPress sizes</a>.</p>
<p>I didn&#8217;t test with any custom image sizes, but I assume it would work as well.</p>
<p>That will set your Facebook Open Graph image size.</p>
<p>How about the Twitter image size?</p>
<p>Then just swap the filter name from wpseo_opengraph_image_size to wpseo_twitter_image_size :</p>
{{< highlight php "style=pygments" >}}function set_custom_facebook_image_size( $img_size ) {
    return 'large';
}
add_filter( 'wpseo_twitter_image_size', 'set_custom_facebook_image_size' );{{< / highlight >}}
<p>And remember you can go <a href="https://developers.facebook.com/tools/debug/sharing/" target="_blank" rel="noopener">here</a> and see what Facebook is retrieving as your Open Graph image sizes (as well as lots of other information). Hit the Scrape button to have Facebook fetch the information again. Often this is not enough and you will have to wait 24 hours for Facebook to clear it&#8217;s overall cache before you see any changes. Of course, this is only for posts that you have previously shared on Facebook before.</p>
<p>Comment below with any questions. For now, here are 2 FREE Months over at Skillshare. Level up!</p>



