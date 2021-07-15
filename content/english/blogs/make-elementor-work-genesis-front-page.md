---
author: "Travis Rodgers"
categories: ["Coding Tutorials", "Videos"]
date:  2017-09-13T07:52:52Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/how-to-make-elementor-work-with-the-genesis-front-page.jpg"
slug:  "make-elementor-work-genesis-front-page"
tags:  ["Coding Tutorials", "Videos"]
title:  "How To Make Elementor Work With The Genesis Front Page"

---


<p>So I have decided to dabble a little with page builders. Seeing that Beaver Builder is all the hype, I decided to try something else&#8230;.namely <a href="/recommends/elementor" target="_blank" rel="nofollow noopener">Elementor</a>.</p>
<p>In order to get acquainted, i&#8217;ve decided to try to recreate some of my pages with Elementor.</p>
<p>My first project: The homepage.</p>
<p>Now my homepage was created with the front-page.php template and its associated widgets.</p>
<p>And from the outset I hit a snag!! When I went it to edit the front page with Elementor I got this message:</p>
<p class="textcenter"><img src="/images/2019/12/make-elementor-work-with-the-genesis-front-page-error-message.jpg" /></p>
<h3>Video Tutorial</h3>

{{< youtube RbyiwwPOfJA >}}

<p>If you prefer not to watch the video or need more instructions, then continue reading.</p>
<h3>What To Do?</h3>
<p>So let&#8217;s think this through. How do we make Elementor work with the Genesis front page? Two thoughts:</p>
<ol>
<li>The &#8216;the_content&#8217; function must be called on the current template. What is the current template?</li>
<li>The current template is front-page.php. (If you are unsure of your template, then go and download the <a href="https://wordpress.org/plugins/show-current-template/" target="_blank" rel="noopener">Show Current Template plugin</a> in WordPress.)</li>
</ol>
<p>Let&#8217;s take a look at the code:</p>
<h3>The Front Page</h3>
<p>The code we need to zoom in on is right at the top of the front-page.php template. It looks like this:</p>
{{< highlight php "style=pygments" >}}add_action( 'genesis_meta', 'executive_home_genesis_meta' );
/**
 * Add widget support for the front page. If no widgets active, display the default loop.
 *
 * @since 3.0.0
 */
function executive_home_genesis_meta() {
	if ( is_active_sidebar( 'home-slider' ) || is_active_sidebar( 'home-top' ) || is_active_sidebar( 'home-top-2' ) || is_active_sidebar( 'home-top-3' ) || is_active_sidebar( 'home-top-4' ) || is_active_sidebar( 'home-portfolio' ) || is_active_sidebar( 'home-cta' ) || is_active_sidebar( 'home-middle' ) ) {
		remove_action( 'genesis_loop', 'genesis_do_loop' );
		add_action( 'genesis_loop', 'executive_home_sections' );
		add_filter( 'genesis_pre_get_option_site_layout', '__genesis_return_full_width_content' );
		add_filter( 'body_class', 'executive_add_home_body_class' );
	}
}{{< / highlight >}}
<p>This function essentially states that if any of the front page&#8217;s widgets are active, then remove the default genesis loop, and add the widgets in its place. It is the genesis loop that calls the_content() function, and since this loop is being removed, Elementor is unable to find the content area.</p>
<p>(The two add filters correlate with the default page layout (full) and the option of adding a class to the body (both of which are found in the Genesis settings). So these are not important to keep either as we will be using Elementor to build the page.)</p>
<p>Since we are going to be building the page with Elementor, we do not need the widgets and can bring back our loop.</p>
<p>So there are two options:</p>
<ol>
<li>We can remove the widgets. This is a &#8220;no&#8221; for me as I have a lot of info there and if I decide to revert I would not want to have to manually insert and populate these again.</li>
<li>We can disable the function. This way we can keep our widgets in place and just not use them.</li>
</ol>
<p>Option #2 it is!</p>
<h3>Make Elementor Work With the Genesis Front Page</h3>
<p>The solution is simple. Just disable the function from being hooked into the page. Here is how to do it with this one line of the above code:</p>
{{< highlight php "style=pygments" >}}//Disable this one line of code with /* and */ on the ends
/*add_action( 'genesis_meta', 'executive_home_genesis_meta' );*/{{< / highlight >}}
<p>Now if you update the template and look at your front page, it will be blank and all set to build. And this is how you make Elementor work with the Genesis front page.</p>
<p><em><strong>Do you use Elementor with Genesis? How have you or how do you make Elementor work with the Genesis front page? I would love to hear your thoughts in the comments below!</strong></em></p>



