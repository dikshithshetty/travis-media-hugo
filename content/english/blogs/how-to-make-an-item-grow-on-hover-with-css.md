---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-09-05T15:06:15Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/grow-on-hover-with-css.jpg"
slug:  "how-to-make-an-item-grow-on-hover-with-css"
tags:  ["Coding Tutorials"]
title:  "How To Make An Item Grow On Hover with CSS"

---
<style>
    .grow { 
transition: all .2s ease-in-out; 
}

.grow:hover { 
transform: scale(1.1); 
}

.shrink { 
transition: all .2s ease-in-out; 
}

.shrink:hover { 
transform: scale(0.9); 
}
    </style>

<p>Here is a simple tweak for you to use on your site to make it a bit more exciting for the user (as long as you don&#8217;t over do it, right?). Find an element or two and make it expand or shrink when the mouse hovers over. Here&#8217;s an example:</p>
<p><img class="grow" src="/images/2019/12/1-hover.jpg" /> <img class="grow" src="/images/2019/12/2-hover.jpg" /></p>
<h3>Make An Item Grow On Hover with CSS</h3>
<p>So how you do make an item grow on hover with css? Simple, two snippets of code that you can use again and again:</p>
{{< highlight php "style=pygments" >}}
function squared(number) {
  return number * number;
}
{{< / highlight >}}

{{< highlight php "style=pygments" >}}
.grow { 
transition: all .2s ease-in-out; 
}

.grow:hover { 
transform: scale(1.1); 
}
{{< / highlight >}}
<p>Now just add .grow as a class to any element and it will do it on hover.</p>
<p>If you want it bigger just up the 1.1 (1.0 being equal size).</p>
<h3>Make An Item Shrink On Hover with CSS</h3>
<p>If you want your element to shrink a bit on hover just create a style for .shrink:</p>
<p><img class="shrink" src="/images/2019/12/1-hover.jpg" /> <img class="shrink" src="/images/2019/12/2-hover.jpg" /></p>
{{< highlight css "style=pygments" >}}.shrink { 
transition: all .2s ease-in-out; 
}

.shrink:hover { 
transform: scale(0.9); 
}{{< / highlight >}}
<p>Now just add .shrink as a class to any element and it will do it on hover.</p>
<p>Keep these in your style.css in case you need them and go ahead&#8230;&#8230;add a little spice to your page.</p>

<div class="youtube-banner textcenter"><a href="http://bit.ly/2OB4Zr5"></a></div>



