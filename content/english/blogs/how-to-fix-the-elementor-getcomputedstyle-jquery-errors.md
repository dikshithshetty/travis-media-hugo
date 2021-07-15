---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-09-23T12:40:10Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/fix-the-elementor-getcomputedstyle-jquery-errors.jpg"
slug:  "how-to-fix-the-elementor-getcomputedstyle-jquery-errors"
tags:  ["Coding Tutorials"]
title:  "How To Fix The Elementor GetComputedStyle jQuery Errors"

---


<p>You Elementor users know you&#8217;ve done it a bunch of times&#8230;&#8230;&#8230;.you know&#8230;&#8230;clicked Edit With Elementor instead of Edit Page up in the admin bar on a non-Elementor post.</p>
<p>Its fine if you have built the page with <a href="/recommends/elementor" target="_blank" rel="noopener">Elementor</a>, but if you have not, then you have just entered Elementor Purgatory, my friend.</p>
<p>Or let me rephrase it this way for those who felt that was a rather strange introductory paragraph:</p>
<p>Have you noticed this error before in your Google Chrome console?</p>
										<p class="textcenter"><img src="/images/2019/12/Fix-The-Elementor-GetComputedStyle-jQuery-Errors-4.png" />											</p>
<p>That&#8217;s Elementor purgatory &#8212; the intermediate state between a WordPress text edit page and an Elementor page build.</p>
<p>Let me explain:</p>
<h3>Video Tutorial</h3>

{{< youtube 8AotvZrSnZ4 >}}

<p>If you prefer not to watch the video or need more instructions, then continue reading.</p>
<h3>Scenario #1</h3>
<p>Let&#8217;s say you created a post with the basic WordPress text editor. You publish it and go on about your business. </p>
<p>Now a week later you realize you should have spiced up the post with Elementor, so you open it up and start dragging and dropping. </p>
<p>But you realize its a bigger task than expected and decide you&#8217;ll do it over the weekend. So you close out the page and don&#8217;t save thinking that it will just revert back to the original post. </p>
<h3>Scenario #2</h3>
<p>Or, you go to edit a non-Elementor post or page and accidentally click Edit With Elementor instead of Edit Page/Post. </p>
<p>You &#8216;X&#8217; out of the page and re-open it and remember this time to hit Edit Page/Post.</p>
<p>In both instances you will end up with multiple GetComputedType jQuery errors in the console. </p>
<p>So what happened?</p>
<p>Well, even though you did not save the page after using Elementor, by clicking Edit With Elementor, you initiated it on the page. Even though your post is coming from what you entered in the original WordPress text editor, Elementor is now looking for elements&#8230;.and can&#8217;t find any!</p>
<p>Thus, the errors. </p>
<h2>How To Fix the Elementor getComputedStyle jQuery Errors</h2>
<p>Good news, it is easy to fix the Elementor getComputedStyle jQuery errors. </p>
<p>Go to the page where you having the errors. Click <em>Edit Post</em> or <em>Edit Page</em> to edit:</p>
<p class="textcenter">										<img src="/images/2019/12/Fix_The_Elementor_GetComputedStyle_jQuery_Errors_3.jpg" />											</p>
<p>Choose <em>Back To WordPress Editor</em>:</p>
<p class="textcenter">										<img src="/images/2019/12/Fix_The_Elementor_GetComputedStyle_jQuery_Errors_2.jpg" />											</p>
<p>And click <em>Update</em> to save your Post or Page:</p>
<p class="textcenter">										<img src="/images/2019/12/Fix_The_Elementor_GetComputedStyle_jQuery_Errors_1.jpg" alt="" />											</p>
<p>And thats it!! </p>
<p>You can do this with any post or page to fix the Elementor GetComputedStyle jQuery errors</p>
<p>Hope this helps!</p>
<p><strong><em>Let me know below if you know of a better way or if you have any further thoughts.</em></strong> </p>



