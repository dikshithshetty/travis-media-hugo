---
author: "Travis Rodgers"
date:  2019-01-30T07:01:16Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/secure-your-wp-config-file.jpg"
slug:  "easily-secure-wp-config-file"
title:  "How to Easily Secure Your wp-config File"

---

<div class="lead-paragraph"><span class="dropcap">T</span>here are a number of ways to add better security to your WordPress site. Moving your wp-config PHP file out of the install is a great place to start. In this article, I&#8217;ll show you two ways to do it.</div><hr class="lead-hr">



<p>Your <a href="https://codex.wordpress.org/Editing_wp-config.php" target="_blank" rel="noreferrer noopener" aria-label="wp-config.php (opens in a new tab)">wp-config.php</a> file stores valuable information such as the location, username, and password of your database, as well as your WordPress authentication keys.</p>



<p>Of course, these are stored as PHP variables and are not shown to the browser, but it&#8217;s always good to go an extra step to secure your WordPress websites.</p>



<p>Here are two ways to do it:</p>



<h2>Two ways to secure your wp-config file</h2>



<h3>1. Change the location</h3>



<p>If WordPress doesn&#8217;t detect this file in the normal install directory, it automatically looks one level up, which is usually a non-public folder.</p>



<p>So a lot of the hosting platforms will have it in a directory like /username/public_html/wp-config.php (with &#8220;username&#8221; normally being your name).</p>



<p>What you can do is move it out into the public_html folder (which is one level up), so that its directory is /username/wp-config.php.</p>



<p>WordPress will still locate your file, and it will be in a &#8220;non-public&#8221; folder.</p>



<h3>2. Change the file name</h3>



<p>The second method is to create a new php file for your wp-config and place an &#8216;include&#8217; in the original file. </p>



<p>So for example, let&#8217;s create a copy of this config file. Then in the /username/ directory, create a folder called dinnertime (or whatever you like). Paste the original wp-config file there and rename it to pizza.php (or again, whatever name you prefer).</p>



<p>We are not moving our original php file yet, but just creating a new copy of it in the /username/dinnertime folder.</p>



<p>Next, remove all the code from the original wp-config file and add an <em><a href="http://php.net/manual/en/function.include.php" target="_blank" rel="noreferrer noopener" aria-label="include (opens in a new tab)">include</a></em> to the relative path of that pizza.php file.</p>



<p>So in the original file you reference the copy by putting:</p>



{{< highlight php "style=pygments" >}}include('/username/dinnertime/pizza.php'){{< / highlight >}}



<h3>Discussion</h3>



<p><strong><em>Have you found another way to do this? How do you best secure your WordPess website? Let me know below.</em></strong></p>



