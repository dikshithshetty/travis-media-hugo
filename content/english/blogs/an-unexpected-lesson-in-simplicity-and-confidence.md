---
author: "Travis Rodgers"
categories: ["Opinion"]
date:  2016-12-28T13:05:00Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/keep-it-simple.jpg"
slug:  "an-unexpected-lesson-in-simplicity-and-confidence"
tags:  ["Opinion"]
title:  "An Unexpected Lesson In Simplicity And Confidence"

---


<p>In my previous post I noted that I did not pass my first assessment at Bloc. Since this happened, I have been really digging in, solving the problems that I got wrong, re-reviewing the material, practicing with online exercises, etc. Most importantly, I worked yesterday with my Bloc mentor and learned a valuable lesson. Let me tell you about it.</p>
<p>I had been stuck on one JavaScript question (<i>before and after code <b>below</b></i>). I had formulated several solutions, all of which were a bit lengthy. In addition, I was all but confident in them.</p>
<p>When I showed the question to my mentor, he first proposed some pseudocode, then filled it in with real code, and produced what would be his answer to it. I sat there waiting for him to add to it, I mean, it was only one line of code!! But as I looked at the code, it made sense. It WAS the solution.</p>
<p>Of course, I had to ask: &#8220;Well what if we wanted to check the other three numbers in the array? Wouldn&#8217;t we need a loop in order to search each index to see if any others matched?&#8221;</p>
<p>His response: &#8220;We could, but that is not what the question asked&#8230;&#8230;.It did not ask us to do that.&#8221;</p>
<p>And that was that. And THAT was powerful.</p>
<p>As a newbie, I default to trying to stick to exact formulas or to write a code that looks impressive. However, as one grows and becomes more confident, it is the simplicity of the answer that demonstrates confidence. In other words, as one grows in this field, the aim of coding is simplicity&#8230;&#8230;clarity.</p>
<blockquote><p>Confidence is demonstrated in simplicity. Insecurity is demonstrated in flashy (yet uncertain) complexity.</p></blockquote>
<p>This is golden! Get to the point. Once you are there, stop typing!</p>
<p>Well my redo assessment is today at 3 p.m. I&#8217;ll approach it with this lesson in mind.</p>
<h4><b>The Exercise:</b></h4>
<p>Write a function that takes 2 arguments &#8211; an array of numbers and a number<br />
And returns true if the array contains the number</p>
<p><b><u>My Initial Unsure And Inaccurate Code</u></b></p>
{{< highlight javascript "style=pygments" >}}function numEquals(number){ 
  var array = [3, 5, 7];
  for(var i = 0; i < array.length - 1; i++){
    if(array[i] = number){ 
      return true;
  }else{
      return false;
    }
  }
}{{< / highlight >}}
<p><b><u><br />
</u></b><b><u>My Post Mentor Meeting Code</u></b></p>
{{< highlight javascript "style=pygments" >}}function numEquals(number){
  var array = [3, 5, 7];
    return(array.indexOf(number) >= 0);
}
{{< / highlight >}}
<p><strong><br />
Have you found this to be the case? Share about it below.</strong></p>



