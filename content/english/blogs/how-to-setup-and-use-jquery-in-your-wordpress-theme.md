---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-09-12T10:15:31Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/how-to-setup-and-use-jquery-in-your-wordpress-theme.jpg"
slug:  "how-to-setup-and-use-jquery-in-your-wordpress-theme"
tags:  ["Coding Tutorials"]
title:  "How To Setup And Use jQuery in your WordPress Theme"

---


<div class="lead-paragraph"><span class="dropcap">W</span>hen we think of WordPress, we primarily think blogging, pages, posts, plugins, etc., and eventually we may move on to working with the style.css, templates, functions.php, or other PHP programming.</div><hr class="lead-hr">
<p>But often times last on the list of things to develop in our WordPress site is JavaScript, and more specifically to this post, jQuery.</p>
<p>Maybe its just me but when I think of WordPress, JavaScript just doesn&#8217;t come to mind. Instead it&#8217;s PHP, it&#8217;s template tags, hooks, filters, etc.</p>
<p>Fortunately, if you are running WordPress then you already have jQuery installed and more than likely you already have a JavaScript file or two running in your theme.</p>
<p>Open your functions.php and do a search for .js and you will normally see at least one being enqueued (and from here can see where it is stored in your theme).</p>
<p>Why not use jQuery in your WordPress theme enough, especially if it is already there?</p>
<p>So without further delay, here&#8217;s how to setup and use jQuery in your WordPress theme:</p>
<h3>1. Create Your File</h3>
<p>Create a new, fresh .js file. Usually the .js files in the theme are being used for specific tasks and I always find that its easier to just create a new one for your custom purposes. In fact, just label it custom_javascript.js.</p>
<p>The JS folder is often found in the lib folder within your theme, and can be accessed via FTP. So go ahead and create a new one with your <a href="https://atom.io" target="_blank" rel="noopener">text editor</a> and drag it in.</p>
<h3>2. Enqueue Your File</h3>
<p>In order to link your script to the generated page you must use the <a href="https://developer.wordpress.org/reference/functions/wp_enqueue_script/" target="_blank" rel="noopener">wp_enqueue_script</a> function I n your functions.php.</p>
<p>There are two steps to this: Create the function and add the action.</p>
<p>Remember, the file we created was custom_javascript.js and it was in our theme&#8217;s lib folder. So here is our function:</p>
{{< highlight php "style=pygments" >}}function my_custom_scripts() {
    wp_enqueue_script( 'custom_javascript', get_stylesheet_directory_uri() . '/lib/js/custom_javascript.js', array( 'jquery' ) );
}
{{< / highlight >}}
<p>Next, we need to <a href="https://developer.wordpress.org/reference/functions/add_action/" target="_blank" rel="noopener">&#8220;add action&#8221;</a> which hooks our function on to a specific action:</p>
{{< highlight php "style=pygments" >}}//Links our script to the generated page
function my_custom_scripts() {
    wp_enqueue_script( 'custom_javascript', get_stylesheet_directory_uri() . '/lib/js/custom_javascript.js', array( 'jquery' ) );
} 

//Hooks our function on to a specific action
add_action( 'wp_enqueue_scripts', 'my_custom_scripts' );
{{< / highlight >}}
<h3>3. Writing jQuery with WordPress</h3>
<p>Now you cannot by default use the $ with your jQuery functions in WordPress. It will not works. By default you will have to use the word jQuery in place of the $. For example:</p>
{{< highlight php "style=pygments" >}}//Not accepted by default in WordPress
$(document).ready(function() {
    $("#gform_6 .gform_title").html('<em>Contact Form 1</em>');
});

//It must be this
jQuery(document).ready(function() {
    jQuery("#gform_6 .gform_title").html('<em>Contact Form 1</em>');
});
{{< / highlight >}}
<p>I don&#8217;t know about you but I really like my dollar signs. Fortunately its a simple fix.</p>
<p>Just wrap your jQuery in this function to use your $ within it:</p>
{{< highlight javascript "style=pygments" >}}(function($) {

   $(document).ready(function() {
       $("#gform_6 .gform_title").html('<em>Contact Form 1</em>');
   });

})( jQuery );{{< / highlight >}}
<h3>Conclusion</h3>
<p>Now that you can setup and use jQuery in your WordPress theme, go use it. <a href="/how-to-add-google-schema-markup-to-custom-menus-in-wordpress" target="_blank" rel="noopener">jQuery is lots of fun.</a></p>
<p>Like I said, it is already there in WordPress just waiting for you to make your site&#8217;s elements come alive and much more.</p>
<p><strong><em>Discussion: Do you use jQuery on your site? What do you do with it?</em></strong></p>



