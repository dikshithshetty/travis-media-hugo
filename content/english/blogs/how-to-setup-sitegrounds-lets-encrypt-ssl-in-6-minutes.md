---
author: "Travis Rodgers"
categories: ["Digital Strategy", "Videos"]
date:  2017-09-16T09:14:39Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/Setup-Sitegrounds-Lets-Encrypt-SSL.jpg"
slug:  "how-to-setup-sitegrounds-lets-encrypt-ssl-in-6-minutes"
tags:  ["Digital Strategy", "Videos"]
title:  "How To Setup Siteground's Let's Encrypt SSL In 6 Minutes"

---


<p>First, why should you move your site from http to https? Well, according to <a href="https://www.keycdn.com/blog/http-to-https/" target="_blank" rel="noopener">KeyCDN&#8217;s excellent article</a>, there are five key reasons and I would encourage you to take the time to read it:</p>
<ol>
<li>Performance</li>
<li>SEO and Rankings</li>
<li>Better Referral Data</li>
<li>More Secure</li>
<li>Build Trust and Credibility</li>
</ol>
<p>Those are some heavy hitters there. </p>
<p>So let&#8217;s setup Siteground&#8217;s Let&#8217;s Encrypt SSL!</p>
<h4>SIX MINUTES</h4>
<h4>Lets go!</h4>
<h3>Video Tutorial</h3>

{{< youtube PESBp2jR4ng >}}

<p>If you prefer not to watch the video or need more instructions, then continue reading.</p>
<h2>1. Setup Siteground&#8217;s Let&#8217;s Encrypt SSL</h2>
<p>Log into Siteground, go to the My Account tab, and select the Go To cPanel button:</p>
<p class="textcenter"><img src="/images/2019/12/setup-sitegrounds-lets-encrypt-ssl-1.png" /></p>
<p>No scroll down to the section labeled Security and click on Let&#8217;s Encrypt:</p>
<p class="textcenter"><img src="/images/2019/12/setup-sitegrounds-lets-encrypt-ssl-2.png" /></p>
<p>This will take you to the Let&#8217;s Encrypt setup screen. </p>
<p>From here you need to select your domain at the bottom, enter your email address, and click install to install the SSL certificate.</p>
<p>Once this finishes, you will see your domain under the Installed Certificates section above it. </p>
<p>This means your site will accept HTTPS, but can go either way. In order to enforce the HTTPS we need to slide the HTTPS Enforce slider from off to on. </p>
<p class="textcenter">		<img src="/images/2019/12//setup-sitegrounds-lets-encrypt-ssl-3.png" />		</p>
<p>Now when you go back to your site and refresh you will see that it is now served by the HTTPS protocol. (It may require you to log back in. </p>
<h4>YAY!</h4>
<h4>But wait</h4>
<h2>2. Mixed Content</h2>
<p>What about all those images and links that were previously HTTP? We are forcing the URL to HTTPS, but what about these static files that are still HTTP. </p>
<p>Well, these will give you errors, either errors in your Console or even worse, your images may not show up!</p>
<p>This happens because unsecure HTTP files are being loaded over a secure environment. </p>
<p>But no worries, its an easy fix. </p>
<h2>3. Better Search Replace</h2>
<p>What we need to do now is sift through our database, which houses our posts and more, and change those HTTP links, etc. to HTTPS. </p>
<p>So go to your Plugins menu, and Add New. Do a search for a plugin named Better Search Replace:</p>
<p class="textcenter">		<img src="/images/2019/12/setup-sitegrounds-lets-encrypt-ssl-5.png" />		</p>
<p>Install this plugin and activate it. </p>
<p>Now go to Tools &#8211;> Better Search Replace and you will come to this screen:</p>
<p class="textcenter">		<img src="/images/2019/12/setup-sitegrounds-lets-encrypt-ssl-4.png" />		</p>
<p>You want to select all the tables and Search for your URL with the HTTP (http://example.com) and Replace with the HTTPS URL (https://example.com). </p>
<p>Be sure to use your URL!! My URL is used in the photo for an example. </p>
<p>Try a Dry Run first if you like or not, but deselect it to actually make it happen. </p>
<h4>AND THATS IT!</h4>
<h4>Yay again!</h4>
<p>Now your site should look the same. You should see no errors in the Console stating HTTP files are being served over an HTTPS site. </p>
<p>If you are like, &#8220;What is the console?&#8221; then you can try a different method, which is to use a HTTPS validator site such as <a href="https://www.sslshopper.com/ssl-checker.html" target="_blank" rel="noopener">SSL Shopper.</a></p>
<p>In addition, you will want to add a new property in Google Search Console for your HTTPS property. </p>
<p>And thats it! That is how to setup Siteground&#8217;s Let&#8217;s Encrypt in less than 6 minutes&#8230;&#8230;well at least the video was that long!!</p>
<p>In all seriousness, I hope this helped and let me know of any questions or concerns. </p>



