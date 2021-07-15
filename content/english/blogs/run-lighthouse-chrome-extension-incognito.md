---
author: "Travis Rodgers"
categories: ["Digital Strategy"]
date:  2019-02-02T06:45:46Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/lighthouse-chrome-extension-incognito-window.jpg"
slug:  "run-lighthouse-chrome-extension-incognito"
tags:  ["Digital Strategy"]
title:  "How to Run the Lighthouse Chrome Extension in Incognito Window"

---

<div class="lead-paragraph"><span class="dropcap">T</span>o be sure you&#8217;re getting accurate results when using the Lighthouse Chrome extension to audit your webpage, you&#8217;ll need to run it in Incognito Mode. Why? Because the results are (often extremely) skewed by the other &#8220;active&#8221; extension used in the browser. In this article, I&#8217;ll show you how to run it in the Incognito window.</div><hr class="lead-hr">



<p>The Lighthouse audit tool is a great way to check the performance of your website. It runs a series of tests and provides not only a score, but pretty specific feedback regarding performance, accessibility, SEO, etc.  </p>



<p>With the Lighthouse Chrome Extension, this can be as simple as clicking the button to run an audit on any webpage.</p>



<p>But there&#8217;s a problem. If you are like me and make use of a number of other great Chrome extensions, you&#8217;ll probably get this message:</p>



<figure class="textcenter"><img src="/images/2019/12/lighthouse-chrome-extension-incognito.jpg" alt="" /></figure>



<p>Since Lighthouse is run in the browser, other extension can often interfere with its accuracy. (I&#8217;ve seen as much as 50 points difference!). </p>



<p>Okay, but when I open the Chrome incognito browser to run the Lighthouse audit, there are no extensions there. What to do?</p>



<p>Well, the Google Chrome Incognito browser exists to keep the browser from tracking our data. So it makes sense that it disables all extensions as that&#8217;s often what many of them do. So we need to add this extension back.</p>



<h2>Here&#8217;s how to &#8220;enable&#8221; the Lighthouse Chrome extension.</h2>



<ol><li>Open your normal Chrome browser, click the menu button (three dots at the top right). Then go to More Tools > Extensions</li><li>Scroll to the Lighthouse Chrome extension and click Details</li><li>Now enable the setting &#8220;Allow in Incognito&#8221;</li></ol>



<figure class="textcenter"><img src="/images/2019/12/lighthouse-chrome-extension-allow-in-incognito-mode.jpg" alt="" /></figure>



<p>And that&#8217;s it. Now when you open up the Incognito window, the Chrome Lighthouse extension is right there in your menu. And no Grammarly extension to slow it down&#8230;.</p>



<hr class="wp-block-separator"/>



<p>Here&#8217;s some more information on the new Lighthouse tool if you&#8217;re new to it:</p>

{{< youtube NoRYn6gOtVo >}}



