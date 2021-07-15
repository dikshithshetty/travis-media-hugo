---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-01-10T14:51:20Z
description:  ""
draft:  false
images:  
 - "/images/2019/12/html-node-copy.png"
slug:  "a-simple-and-practical-explanation-of-firstchild-childnodes-nodevalue"
tags:  ["Coding Tutorials"]
title:  "A Simple and Practical Explanation of firstChild, childNodes, nodeValue"

---


<p>[dropcap]I [/dropcap]recently had an exercise where I was asked to manipulate nodes using firstChild, childNodes, and nodeValue. In my search to better understand these I found many sites explaining the technical jargon behind them and also providing somewhat complex examples of their uses.</p>
<p>However. I was not able to find a simple, practical, &#8220;newbie&#8221; example in order to better understand the root concept itself.</p>
<p>So in my failure to find this, I decided to write a brief post showing and explaining these three properties <em>in use</em>.</p>
<h3>Our HTML Example</h3>
<p>So let&#8217;s start with this HTML file. We will access certain nodes within this file using firstChild, childNodes, and nodeValue:</p>
{{< highlight markdown "style=pygments" >}}
  
    <head>
        <nav class="nav-item">
            <a href="#">Menu Item</a>
        </nav>
    </head>
  
    <body>
    <section>
        <div>  
            <a href="#">Link 2</a>
        </div>
      
        <div>  
            <a href="#">Link 3</a>
        </div> 
      
        <div>  
            <ul>
                <li>First</li>
                <li>Second</li>
                <li>Third</li>
                <li>Fourth</li>
            </ul>
        </div>
      
        <div>  
            <a href="#">Link 4</a>
        </div>
    </section>
    </body>

</html>
{{< / highlight >}}
<p>So at a quick glance, we have four links and an unordered list with four list items.</p>
<h3>firstChild</h3>
<p>Let&#8217;s look at this Script:</p>
{{< highlight markdown "style=pygments" >}}var firstExample = document.getElementsByTagName('a')[1];
firstExample.firstChild.nodeValue = "Link 10";{{< / highlight >}}
<p>For our first example we create a variable called firstExample that will access the second link on the page (note the &#8216;a&#8217; tag and the [1] (because we start at 0, this will be the second link).</p>
<p>We then take this variable and add on .firstChild. This will look at this &#8216;a&#8217; tag and access it&#8217;s first child which is going to be the link name.</p>
<p>We then add on .nodeValue which will access the value of this firstChild which is the text, &#8216;Link 2&#8217;.</p>
<p>Finally we take that nodeValue and change it to say &#8216;Link 10&#8217; instead.</p>
<h3>childNodes</h3>
<p>Next, we will look at this Script:</p>
{{< highlight javascript "style=pygments" >}}var secondExample = document.getElementsByTagName('ul')[0];
secondExample.childNodes[1].innerText = 'Check it out';{{< / highlight >}}
<p>For our second example we create a variable called secondExample that will access the very first &#8216;ul&#8217; tag on the page (note the [0]).</p>
<p>We then take this variable and add on .childNodes. This will look at this &#8216;ul&#8217; tag and give us access to its children (the list items).</p>
<p><strong>Important: Why did we not use [0] for the first child node? Because, this actually gives us access to the whitespace between the end of the &#8216;ul&#8217; tag and the first &#8216;li&#8217; tag (an explanation of this can be abundantly found on a Google search). So [0] gives us whitespace, [1] gives us the first item, [2] gives us the next whitespace, [3] gives us the second item, etc. From what I have read this varies in different browsers???? </strong></p>
<p>We then add on .innerText which will access the value of this childNode, which is the first list item called &#8216;First.&#8217;</p>
<p>Finally we take that text and  change it to say &#8216;Check it out&#8217; instead.</p>
<h3>nodeValue</h3>
<p>So what if I enter this:</p>
{{< highlight javascript "style=pygments" >}}var thirdExample = document.getElementsByTagName('a')[2];
thirdExample.nodeValue = "The Third link";{{< / highlight >}}
<p>Will this work? Will this change the text of the third link to &#8216;The Third Link&#8217;?</p>
<p>No it will not.</p>
<p>Why?</p>
<p>Because the nodeValue is the anchor tag (an element). If you change the second line to say alert(thirdExample.nodeValue);, then you will get null. You cannot treat an element (anchor tag) like text. If you put in nodeName in the place of nodeValue, you can see it return an &#8216;A&#8217; telling us it is an anchor tag.</p>
<p>So what we need to do is look at the nodeValue of the firstChild of the anchor tag, and it will give us access to the actual text of the link as seen here:</p>
{{< highlight javascript "style=pygments" >}}var thirdExample = document.getElementsByTagName('a')[2];
thirdExample.firstChild.nodeValue = "The Third link";{{< / highlight >}}
<h3>Result</h3>
<p>Here is a snapshot of the changes we made above:</p>
<p class="textcenter"><img src="/images/2019/12/nodes.jpg" /></p>
<p>In addition, here is a <a href="http://jsbin.com/ruwodiluco/edit?js,output" target="_blank">link to this exercise in JS Bin</a> so that you can manipulate these yourself.</p>
<h3>Conclusion</h3>
<p>I hope the article was helpful for those of you new to these property types. <strong>Please feel free to add to the dialogue in the comments below!!</strong></p>
<p>**This article is to provide basic and practical examples of these properties for those who may be new to them. There is of course much more to be said (such as exceptions, technical considerations, etc.), however, this was not the intention of the article, and there are many sites out there to explain these in more depth.</p>



