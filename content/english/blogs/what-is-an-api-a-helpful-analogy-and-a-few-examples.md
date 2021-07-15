---
author: "Travis Rodgers"
categories: ["Technical Nerd Talk"]
date:  2019-01-17T07:01:15Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/what-is-an-api.jpg"
slug:  "what-is-an-api-a-helpful-analogy-and-a-few-examples"
tags:  ["Technical Nerd Talk"]
title:  "What is an API? A helpful analogy and a few examples"

---
 
<div class="lead-paragraph"><span class="dropcap">W</span>hat is an API? Sometimes it can be hard to explain or even to understand the concept well. In this post, I want to share a very helpful analogy that I came across to help clear up the concept for you.</div><hr class="lead-hr">



<p>Let&#8217;s face it: Some of us developers have no clue how to really answer the question, What is an API?</p>



<p>We code day in and day out and since we never have to deal with any API, we put it on that list of things we&#8217;ll figure out later. </p>



<p>And it&#8217;s okay to figure it out later. Maybe your job or daily &#8220;thing&#8221; doesn&#8217;t involve APIs at all.</p>



<p>Regardless, I want to take a minute to give you an analogy I read recently to help you out if you ever have to explain it to someone else, and even if you just need a way of understanding the concept better.</p>



<h2>What is an API? The Analogy</h2>



<p>I read this in a book called <a href="https://amzn.to/2Dhik2J" target="_blank" rel="noreferrer noopener" aria-label="&quot;Learning WordPess REST API&quot; by PACKT Publishing (opens in a new tab)">&#8220;Learning WordPess REST API&#8221; by PACKT Publishing</a>. And I&#8217;ll quote here:</p>



<blockquote class="wp-block-quote"><p>In simple words, an application programming interface lets you establish a connection or link between two different types of software. For instance, your computer has a USB port, which is essentially meant for connecting USB storage devices such as flash drives or USB hard disks. However, you can connect virtually any type of USB hardware to the portprinters, smartphones, tablets, and so on. As such, think of the USB port as an API for letting you connect different types of devices to your computer and allowing your computer to interact with the concerned devices accordingly. Much like a USB port facilitates the exchange of data between two physical devices, an API facilitates the exchange of data between two different types of software.</p><cite>&#8211; Learning WordPress REST API by Sufyan bin Uzayr</cite></blockquote>



<p>So with our USB ports, we plug up USB drives, printers, phone chargers, cameras, etc. and they all, despite being different, can &#8220;talk&#8221; to our computer via the USB port. In this way, the USB port is much like an API.</p>



<p>So, What is an API? Use and reference this USB port analogy.</p>



<h2>Common uses of APIs</h2>



<p>We use APIs daily. When we are registering on a site and it allows us to login via Facebook or Google. API! Think about the apps you use&#8230;do any of these have Integrations (with Google calendar, Stripe, etc.) API!</p>



<h4>GitHub API</h4>



<p>Do you have a Github account? If so, type <em>https://api.github.com/users/yourusername </em><br>in the browser (replacing yourusername with your actual username). You will receive some JavaScript Object Notation (JSON) data about your account. If you were building an app that needed to access Github data, you could make a request for it this way. Add in some authentication and you could send data and even update data in your account (or any user that uses your app could do for their own account).</p>



<p>**Side note: JSON is great because it is both machine readable AND human readable. Also, many popular programming languages offer their own interpreters to parse the JSON making it great for cross platform interaction.</p>



<h4>WordPress API</h4>



<p>Another example: The WordPress REST API.  If I wanted to GET the posts from my own website I can simply make a request to https://travis.media/wp-json/wp/v2/posts. Try it with your site, just change the domain name. (Look like gibberish? Download the <a href="https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa?hl=en" target="_blank" rel="noreferrer noopener" aria-label="JSON Formatter Chrome extension (opens in a new tab)">JSON Formatter Chrome extension</a> to see it parsed.)</p>



<h4>YNAB API</h4>



<p>In a final example, <a rel="noreferrer noopener" aria-label="YNAB (the best budgeting app of them all) (opens in a new tab)" href="https://ynab.com/referral/?ref=FNjd2k5ZDZcKgYsj&amp;utm_source=customer_referral" target="_blank">YNAB (the best budgeting app of them all)</a> recently opened up <a rel="noreferrer noopener" aria-label="its API (opens in a new tab)" href="https://api.youneedabudget.com/" target="_blank">its API</a>. </p>



<p>Let&#8217;s say I wanted to create an app that gives the user a visual dashboard of their finances with dials and buttons, etc. that was more appealing than the YNAB interface.</p>



<p>I could talk to the YNAB API and make GET requests to pull data, POST requests to send data, PUT to update data, and DELETE to delete data.</p>



<p>So I could pull data and show it with some sort of dials. I could list the unapproved transactions and approve them from my applications. I could add new categories, delete new categories, etc., etc. You get the point. </p>



<h3>Conclusion</h3>



<p>That&#8217;s as far as I want to go with it in this post. Hopefully, this analogy will help you out when explaining, <em>What is an API?</em>, to others and even perhaps helping with getting a clearer understanding in your own head about it. Thanks for reading.</p>



