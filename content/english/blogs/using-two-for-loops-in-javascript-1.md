---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-01-13T13:18:27Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/two-for-loops-1-1.jpg"
slug:  "using-two-for-loops-in-javascript-1"
tags:  ["Coding Tutorials"]
title:  "Using Two For Loops In JavaScript: Part 1"

---


<p>So here is an array:</p>
{{< highlight javascript "style=pygments" >}}var array = [3, 2, 3, 5, 5, 7, 5, 1];{{< / highlight >}}
<p>There are times when you will need to loop through this array comparing one number with the other numbers. For instance, you start with 3 and compare it with 3, then 2, then 3, then 5, then 5, etc. until you get to the end.</p>
<p>Next, you may want to move to the second number and cycle through the numbers again. So you would take 2 and compare it with 3, then 2, then 3, then 5, then 5, etc. until you get to the end.</p>
<p>This is very useful and very common. So, how do we do this?</p>
<p>We do this by using two <em>for</em> loops.</p>
<h3>The First Loop</h3>
<p>The first loop will cycle us through the numbers. This is just a standard <em>for</em> loop:</p>
{{< highlight javascript "style=pygments" >}}for(var i = 0; i < array.length; i++){
    // do something
}{{< / highlight >}}
<p>For those unfamiliar with <em>for</em> loops, this loop basically says three things:</p>
<ol>
<li><strong>var i = 0</strong> sets the variable before the loop starts (NOTE: This is a ZERO and not the letter O). So the variable i will equal 0.</li>
<li><strong>i < array.length</strong> is the &#8220;if&#8221; statement. If i is less than the length of the array, the loop will execute.</li>
<li><strong>i++</strong> says that after the loop does something, the variable i will increment one (0 will become 1).</li>
</ol>
<h3>The Second Loop</h3>
<p>The second loop is going to look the same but with a different variable. Lets make that different variable the letter j:</p>
{{< highlight javascript "style=pygments" >}}for(var j = 0; j < array.length; j++){
    // do something
}{{< / highlight >}}
<p>The second loop will also cycle through the numbers but there are <em><strong>a few differences</strong></em>.</p>
<ol>
<li>This loop is nested <strong>inside</strong> the first <em>for</em> loop. This means the first loop will execute, move to the second loop where the second loop will continue to loop until completion, and then the first loop will execute again, move to the second loop where the second loop will loop until completion, etc., etc., until the first loop is completed.</li>
<li>The variable is different. This allows the second loop to move through the array independent of the first loop&#8217;s variable.</li>
</ol>
<h3>The Two For Loops Together</h3>
<p>So here are both loops together:</p>
{{< highlight javascript "style=pygments" >}}for(var i = 0; i < array.length; i++){
    for(var j = 0; j < array.length; j++){
        // do something
    }
}{{< / highlight >}}
<p>So lets look at our array again:</p>
{{< highlight javascript "style=pygments" >}}var array = [3, 2, 3, 5, 5, 7, 5, 1];{{< / highlight >}}
<ul>
<li>The first loop will start with [0] which is the number 3 (remember in arrays the first number index is 0).</li>
<li>The first loop will sit on the number 3 while the second loop, with the variable j, cycles through all the numbers.</li>
<li>Once all the numbers have been cycled through, the first loop then moves from 0 to 1 (x++), looks at the conditional (is 1 < array.length), and then executes, which looks at the second loop again. The second loop cycles through all the numbers while the first stays on 2. And repeat&#8230;.</li>
</ul>
<h3>A Practical Example</h3>
<p>So what do two <em>for</em> loops look like practically? Well, we will look at a practical example in Part 2.</p>



