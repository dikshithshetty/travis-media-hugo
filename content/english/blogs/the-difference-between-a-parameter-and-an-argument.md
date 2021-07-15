---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-01-23T13:41:13Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/difference-between-a-parameter-and-an-argument-featured-image.jpg"
slug:  "the-difference-between-a-parameter-and-an-argument"
tags:  ["Coding Tutorials"]
title:  "The Difference Between a Parameter and an Argument"

---


<p>Is there a difference between a <span style="text-decoration: underline;">parameter</span> and an <span style="text-decoration: underline;">argument</span>? Are they synonymous with one another?</p>
<p>I&#8217;ve been guilty of it myself when talking about functions&#8230;&#8230;using the words parameter and argument interchangeably.</p>
<p>I mean, they both come after the function name in the parentheses right?</p>
<p>Right!</p>
<p>Then what&#8217;s the difference between a parameter and an argument?</p>
<h3>Our Example</h3>
<p>Let me explain in this very simple function:</p>
{{< highlight php "style=pygments" >}}
function squared(number) {
  return number * number;
}
{{< / highlight >}}
<h3>Parameter Explained</h3>
<p>The parameter of this function is <strong>number</strong>.</p>
<p><strong>This is the variable name used to reference the arguments passed to the function.</strong></p>
<p>It can be named anything, but you should choose something relevant.</p>
<h3>Argument Explained</h3>
<p>The argument of this function will be what you actually pass to it.</p>
<p>When we call this function we will pass a real number as an argument like this:</p>
{{< highlight php "style=pygments" >}}
squared(4);
{{< / highlight >}}
<p>The argument is 4 and the function will return 16.</p>
<p>If we passed 5 as the argument, the function will return 16.</p>
<h3>Conclusion</h3>
<p>As you see, this is a subtle but important difference in terms.</p>
<p>Our function has <strong>number</strong> as the <span style="text-decoration: underline;">parameter</span> used to reference the <span style="text-decoration: underline;">argument</span> we will pass to the function (4 or 5 as our examples above).</p>
<p>Hope this helps next time we use the two terms.</p>
<p><em><strong>Have you mixed these two up before? I think we all have!!</strong></em></p>
<p>&nbsp;</p>



