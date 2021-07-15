---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-01-20T00:01:20Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/students.jpeg"
slug:  "spark-child-interest-in-coding-with-silly-program"
tags:  ["Coding Tutorials"]
title:  "Spark A Child's Interest In Coding With This Silly Program"

---


<p>I keep hearing stories about kids learning to code and it really puzzles me. Maybe because I could not see myself doing it as a pre-teen/teenager (which of course is NOT a good way to gauge things). Perhaps it was because I did not know anyone who coded nor did anyone introduce me to it. Perhaps it was because computers were not as normative as they are now, I mean, it wasn&#8217;t until high school that I even used the internet (i&#8217;m 35)?</p>
<p>Whatever the case, I seem to have a hard time imagining my 8-year-old daughter getting into strings or functions or arrays, etc.,</p>
<h3>But then&#8230;.</h3>
<p>But then there are a few books I have come across recently, in particular <a href="http://amzn.to/2jDN4kP" target="_blank">JavaScript for Kids: A Playful Introduction to Programming</a>, that have revved up the cognitive cogwheels. For some reason I feel like this book would have appealed to me if I were young again. And to be honest, I find it a refreshing book even now, especially with all of the practical things you build in it.</p>
<h3>The Test</h3>
<p>Well, just to test the interest, I decided to try something out on my daughter.</p>
<p>I created a simple and silly prompt/alert program in JavaScript called Travis&#8217;s Truth Machine. Basically, you click the button and it asks you for a name. If the name happens to be any one of my four children, or my wife, it gives a funny answer such as, &#8220;Your name means Dirty Frog&#8221; or for me it is &#8220;Your name is the best ever.&#8221;</p>
<h3>The Response</h3>
<p>I let them see it and it was a hit! It was the craze for the day. There just may be some truth to kids and coding, especially if there is a practical benefit (even though it was a silly game).</p>
<p>Try it out with your kids. It&#8217;s very basic, yet it just may be that spark that directs them toward an interest in coding.</p>
<p>Here is the JavaScript code I created, adding some simple HTML so I could make it look a tad more appealing. I changed some of the names and alerts, so customize them accordingly:</p>
{{< highlight html "style=pygments" >}}<html>
  <body>
    <h2>Travis's Truth Machine<h2>
    <h4><em>I will tell you the truth about your name!</em></h4>
    
    <button onclick="nameGame()">Click for the truth</button>

  <script>
    function nameGame() {
    var name = prompt("Hello, what is your name?");
    if(name == "Travis"){
      alert("Awesome name");
    }else if(name == "Jenny"){
      alert("Your name means Smelly Frog");
    }else if(name == "Ben"){
      alert("Your name is Weird");
    }else if(name == "Timothy"){
      alert("Your name means Swinging Monkey");
    }else if(name == "Suzie"){
      alert("Wonderful name!");
    }else if(name == "Bobby"){
      alert("Your name means Wet Dog");
    }else if(name == "Kate"){
      alert("Your name smells like garlic");
    }else{
      alert("Your name is boring");
  }
}		
  </script>

  </body>
</html>{{< / highlight >}}
<p>Add some CSS. Let your kids see you add more to it and make changes.</p>
<p>I hope they will find something like this as interesting as mine found it.</p>
<p>Happy coding!</p>
<p><strong>What are your experiences with children and coding? I would love to hear in the comments below.</strong></p>



