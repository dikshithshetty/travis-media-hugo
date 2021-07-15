---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-01-03T12:26:00Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/you-dont-know-js.png"
slug:  "two-important-javascript-loops-and-a-book-recommendation"
tags:  ["Coding Tutorials"]
title:  "Two Important JavaScript Loops And A Book Recommendation"

---


<p>Though I was understanding the beginning concepts of JavaScript well and able to follow along with the lessons, there was undoubtedly something missing. Well, I think I have found it.</p>
<h3>A Helpful Book</h3>
<p>I am not sure where the recommendation came from, probably a Medium article, but there happen to be a series of books called &#8220;<a href="https://www.amazon.com/You-Dont-Know-JS-Going-ebook/dp/B00V20DQU8/ref=dp_kinw_strp_1" target="_blank">You Don&#8217;t Know JS</a>,&#8221; by Kyle Simpson. The first book of the series is called, &#8220;Up and Going,&#8221; and is intended for JS beginners (like me). Best of all it is <a href="https://www.amazon.com/You-Dont-Know-JS-Going-ebook/dp/B00V20DQU8/ref=dp_kinw_strp_1" target="_blank">FREE</a> for the Kindle as well as <a href="https://github.com/getify/You-Dont-Know-JS" target="_blank">Free on Github</a>.</p>
<p>This book is highly recommended and very helpful if you started your study of JavaScript on a platform such as CodeSchool or Free Code Camp. These sites are great and will get you on your feet, but they tend to leave gaps in the fundamentals that are key to growing faster in your understanding of JS.</p>
<h3>Combining Similar Concepts</h3>
<p>This book may seem basic for some, but basic was just what I needed. Also, many concepts intersect to help you broaden your understanding faster &#8230;&#8230;. such as this:</p>
<p>Let&#8217;s look at a While loop (given as an example in above book):</p>
{{< highlight javascript "style=pygments" >}}while (numOfCustomers > 0) {
  
  console.log( "How may I help you?" );

    // help the customer...

  numOfCustomers = numOfCustomers - 1;{{< / highlight >}}
<p>The above javascript loop sets the condition from the outset: If the number of customers is greater than 0, then do something.</p>
<p>Well what if you wanted to do something <i>one time, first</i>, and then consider the condition?</p>
<p>Basically it would be the same thing, but reversed. This is called a (do..While) loop:</p>
{{< highlight javascript "style=pygments" >}}do {

  console.log( "How may I help you?" );

    // help the customer...

  numOfCustomers = numOfCustomers - 1;

} while (numOfCustomers > 0);{{< / highlight >}}
<p>The above JavaScript loop does something first, and then sets the condition afterwards. The former does something if a condition is met and will continue to do something if the condition is met, while the latter does something <i>one time first</i> before considering the condition.</p>
<p>I had not heard of a do..While loop yet until they tied the two together in this book. If one understands a While loop already, then something like a do..While loop is retained instantly.</p>
<p>Anyways, the book is free! If you are a JavaScript newbie get it!</p>
<p><b>Have any other JavaScript books been helpful to you. Please share them below in the comments!!</b></p>



