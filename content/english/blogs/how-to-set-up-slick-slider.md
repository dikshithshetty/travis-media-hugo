---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2019-05-13T06:55:04Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/slick-slider-carousel-set-up.jpg"
slug:  "how-to-set-up-slick-slider"
tags:  ["Coding Tutorials"]
title:  "How to Set Up Slick Slider (with arrows)"

---

<div class="lead-paragraph"><span class="dropcap">T</span>he Slick Slider library is a solid option for displaying slideshows on your website and my go-to solution the majority of the time. In this post, I&#8217;ll show you how to set it up for your next project.</div><hr class="lead-hr">



<p>Being a developer I personally hate slider plugins. In my opinion they give you so many options that you end up not being able to maintain without having to do all kinds of magic. </p>



<p>They are supposed to make it easy for the end user, the non-technical WordPress blogger looking to maintain their site themselves, but it ends up being overkill as it seeks to provide hundreds of options that sliders really shouldn&#8217;t have. </p>



<p>That&#8217;s why I prefer the Slick Slider carousel plugin by Ken Wheeler. Not the &#8220;plugin&#8221; that you install and activate, but the library itself. </p>



<p>Let me show you how to set it up:</p>



<h2>How Do I Install It</h2>



<p>I always prefer to pull the files into my project. That way I have complete control to customize and 100% uptime. There is a simple CDN option and NPM as well.</p>



<h4>1. Place the files in your project</h4>



<p><a href="https://kenwheeler.github.io/slick/#go-get-it" target="_blank" rel="noreferrer noopener" aria-label="Go to the website, click on Get It Now (opens in a new tab)">Go to the website, click on Get It Now</a>, and that will shoot you down to a Download button. Download the files. </p>



<p>Go to the Slick folder and choose either the minified slick.min.js file or if you are using a task manager like Gulp then just choose slick.js and put it in your Gulp process to be minified. </p>



<p>Next, you want to add the slick and slick-theme stylesheets to your project. If you are using Sass, then grab the slick.scss and slick-theme.scss and drop it in your Gulp process (or Grunt, Webpack, etc.). If you are not, the grab the regular CSS versions. Be sure to reference/<a rel="noreferrer noopener" aria-label="enqueue (opens in a new tab)" href="https://developer.wordpress.org/reference/functions/wp_enqueue_script/" target="_blank">enqueue</a> them so your project recognizes them. </p>



<h4>2. Add the fonts folder</h4>



<p>Take the ajax-loader.gif and drag it to the provided fonts folder. Then add the fonts folder to your project. Add it in, or someone close to, where you put the slick slider stylesheets/script files so you can reference it easily. </p>



<h4>3. Tweak the files</h4>



<p>If you open up slick-theme.css or slick-theme.scss, you will see that the fonts folder is being referenced. In the font-face with css (src: url(&#8216;./fonts/slick.eot&#8217;)) and in variables with scss($slick-font-path: &#8220;./fonts/&#8221; !default;).</p>



<p>You will also see that the ajax-loader.gif is being referenced with a relative path. </p>



<p>You will need to adjust these paths depending on where you placed your fonts folder.</p>



<h2>How Do I Use It</h2>



<p>Many ways!. Here&#8217;s a simple example. </p>



<p>Say I want to have a slideshow of three photos. In my html I can put something like:</p>



{{< highlight markdown "style=pygments" >}}<div id="homepage-slider">
    <div class="slider-hero">
        <div>
            <img src="/images/2019/12/stock-photo.jpg" />
        </div>
        <div>
            <img src="/images/2019/12/stock-photo.jpg" />
        </div>
        <div>
            <img src="/images/2019/12/stock-photo.jpg" />
        </div>
    </div>
</div>{{< / highlight >}}



<p>That gives me my three photos on the page. </p>



<p>Now I need to use JS to initialize the slider functionality like (and do this in a separate JS file. Create one called custom.js or something like that, and be sure to reference/enqueue the file):</p>



{{< highlight javascript "style=pygments" >}}(function($) {
    $(document).ready(function() {
        $('.slider-hero').slick({
            dots: true,
            infinite: true,
            cssEase: 'linear',
            swipe: false,
        });
    });
	
})( jQuery );{{< / highlight >}}



<p>See how I am targeting that slider-hero class? </p>



<p>And the options like dots, infinite, etc. are just slider options and these are all<a rel="noreferrer noopener" aria-label=" explained in the documentation (opens in a new tab)" href="https://kenwheeler.github.io/slick" target="_blank"> explained in the documentation</a>, along with further options like filtering, syncing, etc. </p>

<div class="youtube-banner textcenter"><a href="http://youtube.com/c/travismedia?sub_confirmation=1"></a></div>

<h2>Where Are My Slick Slider Arrows?</h2>



<p>Slick slider provides you with some arrows. You&#8217;ll find these on line 91 and 95 of slick-theme.css or as a variable in slick-theme.scss.</p>



<p>These look bad. I never liked them. Thus, I went out and found much better replacements arrows. </p>



<p>Here they are for you to use as well:</p>



<p><a rel="noreferrer noopener" aria-label="Next arrow (opens in a new tab)" href="/images/2019/12/next-arrow.svg" target="_blank">Next arrow</a><br><a rel="noreferrer noopener" aria-label="Previous arrow (opens in a new tab)" href="/images/2019/12/previous-arrow.svg" target="_blank">Previous arrow</a></p>



<p>So upload these SVG arrows to your project. Then jump back to your slick-theme.scss or slick-theme.css and replace the arrows in the pseudoclass with these instead.</p>



<h3>Conclusion</h3>



<p>So that&#8217;s how you can set up Slick Slider in your next project. It&#8217;s simple, lightweight, and can do 99% of what you&#8217;ll need with a slider without all the bload and confusion that you find out there with other plugins. Enjoy.</p>



