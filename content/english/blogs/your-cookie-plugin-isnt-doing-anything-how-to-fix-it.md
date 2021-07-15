---
author: "Travis Rodgers"
categories: ["Digital Strategy"]
date:  2018-06-02T10:16:50Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/cookie-plugin-featured.jpg"
slug:  "your-cookie-plugin-isnt-doing-anything-how-to-fix-it"
tags:  ["Digital Strategy"]
title:  "Blogger, your Cookie Plugin isn't doing anything! Here's how to fix it"

---


<p>Now that the GDPR D-Day has arrived, everyone has a cookie plugin. These cookie policy plugins have popped up everywhere in the WordPress plugin repository. But here&rsquo;s the million dollar question: Are these plugins by default doing anything after activation or are they simply just displaying messages? Let&rsquo;s take a look.</p>
<p class="textcenter"><img data-rjs="2" title="cookie plugin pinterest" src="/images/2019/12/cookie-plugin-pinterest.jpg" style=""></p>
<p>Now I&rsquo;ve tried a number of cookie plugins on my own site and most of them say something like &ldquo;Just activate the plugin and you&rsquo;re done!&rdquo; It&rsquo;s that simple!</p>
<p>Wrong.</p>
<p>One of the more popular of the cookie plugins is <a href="https://wordpress.org/plugins/cookie-notice/" rel="nofollow" target="_blank">Cookie Notice by dFactory</a> with over 700,000 active installations and lots of great reviews. And it&rsquo;s a good plugin and one that I would recommend. But what does it do by default?</p>
<p>Well, I chose the Cookie Notice plugin as my test subject and here are the findings:</p>
<h3>The Cookie Notice plugin activated</h3>
<p>So what happens when you activate the Cookie Notice plugin?</p>
<p>You get a notification bar displaying a message and your desired buttons. For example:</p>
<p class="textcenter"><img alt="cookie plugin banner" src="/images/2019/12/cookie-plugin-banner.png" /></p>
<p>If you are using Chrome, and you check in Settings &ndash;> Advanced &ndash;> Content Settings &ndash;> Cookies &ndash;> see all cookies and site data &ndash;> and search for the site, you will see that there are still cookies being set. Nothing different here.</p>
<p>So for all the people who installed the plugin, it is technically doing nothing but displaying a message. If the visitor does not accept, it still sets cookies.&nbsp;</p>
<p>So it&rsquo;s a placebo.</p>
<h3>The purpose of the Cookie Notice plugin and your cookie plugin</h3>
<p>Now I have only tried a few of these cookie plugins, but the purpose seems to be the same:</p>
<p><strong>To block desired scripts until the visitor accepts your disclaimer.</strong></p>
<p>This may be Google Tag Manager, Crazy Egg, Google Analytics, or whatever script you are pulling into the page.&nbsp;</p>
<p>So essentially you can block something like Google Analytics from tracking until your site visitor accepts the agreement.&nbsp;</p>
<h3>So How Do You Set Up Your Cookie Plugin Then?</h3>
<p>In the case of the Cookie Notice plugin by dFactory, you need to look in the Settings panel.&nbsp;</p>
<p>There is a text area where you will enter in the scripts you want to block:</p>
<p class="textcenter"><img alt="cookie plugin block scripts" src="/images/2019/12/cookie-plugin-block-scripts.png" /></p>
<p>So normally, where you would insert your third-party scripts like Google Analytics, etc. into your header somewhere, you would put them in this box instead.</p>
<p>Let me explain what this does:</p>
<ol class=""><li>When the visitor accepts the cookies, it adds a new cookie to the browser called cookie_notice_accepted.</li>
<li>Cookie Notice has a function by which it checks if the cookies are accepted called cn_cookies_accepted().</li>
<li>By inserting your script(s) in this text box, you are conditionally blocking them from loading until the visitor has accepted the disclaimer (when the cn_cookies_accepted() function sees the cookie_notice_accepted cookie).&nbsp;</li>
</ol><p>If your scripts are being loaded through an add_action hook or something similar and you need to block this elsewhere, you can use the following PHP code:</p>
{{< highlight php "style=pygments" >}}
if (function_exists('cn_cookies_accepted') && cn_cookies_accepted()) {
    ...ENTER YOUR SCRIPTS HERE 
}
{{< / highlight >}}
<p><strong>ONE MORE THING:</strong></p>
<p>Be sure you check the box &ldquo;Enable to reload the page after cookies are accepted&rdquo; so when they accept, the page will reload with the scripts running again.&nbsp;</p>
<p>The scripts will now load normally until the cookies expire (you can set this duration too) or until they clear them from your browser.&nbsp;</p>
<h4>How To Handle Visitors Not Accepting Your Cookies</h4>
<p>How will your analytics or other tracking applications fare without being able to track visitors? Should you allow visitors to browse your site while refusing cookies to be set? I don&rsquo;t know. Share your thoughts in the comments.&nbsp;</p>
<p>Cookie Notice gives the option to allow the visitor to refuse third-party functional cookies. Perhaps if they click the button to refuse, you could redirect them to a page by which you can have them &ldquo;rick-rolled.&rdquo;</p>
<p>It also gives you the option to &ldquo;accept cookies on scroll,&rdquo; which adds the acceptance cookie if they decide to disregard and scroll the page anyways. Perhaps not the most GDPR-compliant approach, but an option.&nbsp;</p>
<p>Another option is to take a reverse approach and say something like &ldquo;We use cookies on our site to enhance your user experience. Unless you explicitly refuse them, we assume you agree,&rdquo; and then give them the option to refuse.</p>
<p><strong>Either way, how do you handle cookies on your website? Are you blocking scripts? Is your cookie plugin actually doing anything? I would love to discuss it below. </strong></p>



