---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-01-09T14:48:08Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/variable.png"
slug:  "the-importance-of-variable-placement-in-a-javascript-function"
tags:  ["Coding Tutorials"]
title:  "The Importance of Variable Placement in a JavaScript Function"

---


<p>In a JavaScript function, where you place your variables is VERY important. This was indeed an &#8216;aha&#8217; moment for me, and for all the other new programmers out there hopefully this will benefit you.</p>
<h3>The Task</h3>
<p>So my task was to create a function in JavaScript that would look through an array, identify the most recurrent number, and return the amount of recurrences. So if the array was [2, 9, 4, 2, 2], it would recognize that 2 is the most frequent number and return 3 because there are three 2&#8217;s.</p>
<p>After much trial and error I produced this:</p>
{{< highlight javascript "style=pygments" >}}var maximumFrequency = 0;  
var counter = 0;   
function mostRecurrentNumber(array) {
    for (var i=0; i<array.length; i++)  {  
        for (var y=i; y<array.length; y++)  {  
            if (array[i] == array[y]){  
                counter++;  
            if (maximumFrequency<counter)  {  
                maximumFrequency=counter;   
            }  
          }
        }  
      counter=0;
    }  
  return maximumFrequency;
};{{< / highlight >}}
<p>In the above function we created two &#8216;for&#8217; loops that will cycle through all the numbers. So the first loop will look at the first number in the array and trigger the second &#8216;for&#8217; loop that will cycle through all the numbers and compare them to the first number.</p>
<p>If the numbers match, our counter advances to 1. If this counter is more than the maxFrequency, then the maxFrequency takes the counter&#8217;s value. After the second &#8216;for&#8217; loop looks through all the numbers, the counter resets, the first &#8216;for&#8217; loop moves to the second number and the second &#8216;for&#8217; loop cycles through the numbers again to compare. Ultimately at the end, the highest count will give that value to the maxFrequency variable.</p>
<h3>The Complication</h3>
<p>However, this function only worked &#8230;.. halfway. Let me explain:</p>
<p>When I ran this I got 2:</p>
<p>mostRecurrentNumber([3, 6, 4, 4]);</p>
<p>&#8211;>2</p>
<p>Great!</p>
<p>Yet when I tested what would happen on calling the function multiple times (looking to get the answer to the final call), I got 3, when I should have gotten 0:</p>
<p>mostRecurrentNumber([3, 6, 4, 4]);<br />
mostRecurrentNumber([3, 6, 4, 4, 4]);<br />
mostRecurrentNumber([])</p>
<p>&#8211;>3</p>
<p>Why was I not getting 0? And why was I getting 3???</p>
<h3>The Solution</h3>
<p>What I came to realize was that the maxFrequency variable was keeping the highest value without resetting itself upon re-calling the function.</p>
<p>Why in the world was it doing that?</p>
<p>Take a minute and see if you can figure it out&#8230;&#8230;&#8230;..</p>
<p>&#8230;&#8230;&#8230;&#8230;&#8230;..</p>
<p>Well take a look at the variables. They are outside of the function. Thus the maxFrequency variable was not resetting within the function when it moved to the next call. It was keeping the highest number, which at the end of the three calls would be 3.</p>
<p>Can you see what the solution would be then?</p>
<p>Yes &#8230; move the variables WITHIN the function. Thus, the function when re-called, sets the maxFrequency back at 0. It would look like this:</p>
{{< highlight javascript "style=pygments" >}}function mostRecurrentNumber(array) {
var maximumFrequency = 0;  
var counter = 0; 
    for (var i=0; i<array.length; i++)  {  
        for (var y=i; y<array.length; y++)  {  
            if (array[i] == array[y]){  
                counter++;  
            if (maximumFrequency<counter)  {  
                maximumFrequency=counter;   
            }  
          }
        }  
      counter=0;
    }  
  return maximumFrequency;
};{{< / highlight >}}
<p>The answer to the below example would now be 0:</p>
<p>mostRecurrentNumber([3, 6, 4, 4]);<br />
mostRecurrentNumber([3, 6, 4, 4, 4]);<br />
mostRecurrentNumber([])</p>
<p>&#8211;>0</p>



