---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-01-18T10:30:09Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/learn-to-code-faster-1.jpg"
slug:  "learn-to-code-faster-by-understanding-these-3-concepts"
tags:  ["Coding Tutorials"]
title:  "Learn To Code Faster By Understanding These 3 Concepts"

---


<div class="lead-paragraph"><span class="dropcap">I</span>t's been a little over a year now since I began to take coding seriously (I've a free ebook all about it!). I often think, "What could I have done differently that would have helped me to learn to code faster?"</div><hr class="lead-hr">
<p>I think it&#8217;s very helpful to look back on your coding journey, and try to pinpoint those things you found beneficial and those that were a waste of time. Those positive practice should be shared with those just starting out in hopes to help them learn to code faster without wasting time.</p>
<p>Today I was thinking what I would tell a CodeNewbie (of which I still consider myself) to help them suceed more effectively in their coding journey.</p>
<p>This post looks to answer this thought with three points that I think will help anyone grasp the concept of coding, no matter the language or platform, and ultimately learn to code faster.</p>
<h2>Learn To Code Faster With These 3 Concepts</h2>
<h3>1. Pseudocode</h3>
<p>Anyone with a logical brain can do pseudocode. Actually we do it every day.</p>
<p>When I started to code I just couldn&#8217;t understand pseudocode. Perhaps I was reading the wrong tutorials.</p>
<p>It seemed really difficult because I kept coming to different conclusions than the one teaching it (not knowing that this was okay!).</p>
<p>I was told I needed to paraphrase the code before I actually write it, but then they went on to mention Markdown, and the best way to write it, and I got caught up in all the steps involved and it just seemed something I couldn&#8217;t quite grasp.</p>
<p>A year later I realized I was seriously overthinking it. It&#8217;s rather simple and at the same time extremely helpful.</p>
<p>Think if you had a dentist appointment at 3:00.  Its currently 2:00 and you are already out on the town. You need to get groceries, deposit a check, and make it to the appointment by 3:00.</p>
<p>You might plan things like this:</p>
<ul>
<li>I need to get groceries and deposit a check by 3:00</li>
<li>Which one is futher away? The bank. Go to the bank first.</li>
<li>Which grocery store is closer to the dentist office? Wal-Mart. Go there next.</li>
<li>It will be 2:30 when I arrive at Wal-Mart. The dentist office is 5 minutes away. I will have 25 minutes left to shop.</li>
<li>In order to be done in 25 minutes I can only grab the essentials. Grab the essentials in the grocery section only.</li>
<li>Leave Wal-Mart by 2:55.</li>
<li>Arrive at the dentist office at 3 p.m.</li>
</ul>
<p>Now perhaps that&#8217;s a beastly example, but you get the point. There were no directions involved. There was no exact mileage. There were no additional conditions checking for traffic or road work.</p>
<p>Instead, there was a paraphrased outline of our plan to get groceries, cash a check, and make it to the dentist office within an hour.</p>
<p><strong>Paraphrased</strong>. Thats the key.</p>
<p>Pseudocode is not a programming language. There is no syntax or rules. Its a summary of steps needed to reach a conclusion.</p>
<p>Thats it!! Don&#8217;t overthink it.</p>
<p>And at the same time, do not underestimate it.</p>
<p>It will, without doubt, help you learn to code faster!</p>
<p>Now lets give a coding example:</p>
<p>Lets say you had two forms on your website. Form A and Form B. And you want to get the number of rooms from Form A and repeat a set of fields on Form B based on how many rooms there were on form A.</p>
<p>So if there were 3 rooms in Form A, a section of Form B would repeat 3 times. If there were 2 rooms in Form A, the section in Form B would repeat only 2 times.</p>
<p>Now, to do pseudocode it doesn&#8217;t matter if this is accomplished with PHP, JavaScript, or Python. We don&#8217;t need syntax or code, we just need some paraphrased logic.</p>
<p>Our pseudocode may go something like this:</p>
<ul>
<li>Check to see if there is a Form A</li>
<li>Get the number of rooms from Form A</li>
<li>Create 10 sections in Form B as 10 will be the max number.</li>
<li>Give each section a class like room-1, room-2, room-3, etc.</li>
<li>Take the number of rooms from Form A and loop through Form B hiding the sections that are greater than the number on the class (room-2, room-3, etc.).</li>
</ul>
<p>Thats very basic, but you get the point.</p>
<p>Now that I have some pseudocode, we can take this and use the syntax of our language to make it happen.</p>
<p>How do we do this? What if I don&#8217;t know the language?</p>
<p>No worries! Why? Because all we need to know are the concepts that nearly all code shares i some way:</p>
<p>Lets look at that.</p>
<h3>2. Concepts</h3>
<p>Here is an example:</p>
<p>Javascript has a for loop. You get the hang of that, and then you learn the while loop. Someone has you work on their site and its in PHP. Well, PHP has a for loop&#8230;..and a while loop. Then you begin to explore python and see also that they have a for loop AND a while loop!!</p>
<p>Javascript has an if statement that can be paired with an else if, PHP an elseif, and Python an elsif. Different terms, same concept.</p>
<p>They all three have &#8220;if&#8221; statements.</p>
<p>They all three have strings, variables, methods, functions&#8230;&#8230;.!</p>
<p>What&#8217;s the difference? Syntax!! (Hang on, we will talk about this in the final section.)</p>
<p>The key is to nail down these fundamental concepts and get a good grasp on them.</p>
<p>Here are a few to summarize that you must know:</p>
<h4><a href="http://www.spanishdict.com/answers/102522/in-computer-programming-what-does-string-mean" target="_blank" rel="noopener">Strings</a></h4>
<p>A string is a sequence of characters between two single or double quotes.</p>
<blockquote><p>&#8220;Hello World!&#8221;</p></blockquote>
<h4>Integers</h4>
<p>Integers are numbers (not strings)</p>
<blockquote><p>4</p></blockquote>
<h4><a href="https://en.wikipedia.org/wiki/Variable" target="_blank" rel="noopener">Variables</a></h4>
<p>A symbolic name associated with a value and whose associated value may be changed</p>
<blockquote><p>a = 4<br />
a is the variable</p></blockquote>
<h4>Conditionals / <a href="https://www.pluralsight.com/blog/it-ops/if-statements" target="_blank" rel="noopener">If statements</a></h4>
<p>Tells a program to execute different actions depending on whether a condition is true or false</p>
<blockquote><p>if (10 < 20) {</p>
<p>print(&#8220;This is right!&#8221;)</p>
<p>}</p></blockquote>
<h4>For Loops</h4>
<p>Handy, if you want to run the same code over and over again, each time with a different value.</p>
<blockquote><p>for (i = 0; i < 5; i++) {</p>
<p>text += &#8220;The number is &#8221; + i + &#8220;<br>&#8221;;</p>
<p>}</p></blockquote>
<h4><a href="https://www.cs.utah.edu/~germain/PPS/Topics/while_loops.html" target="_blank" rel="noopener">While Loops</a></h4>
<p>Used to repeat a specific block of code an unknown number of times, until a condition is met.</p>
<blockquote><p>while (i < 10) {<br />
text += &#8220;The number is &#8221; + i;<br />
i++;<br />
}</p></blockquote>
<h4>Functions</h4>
<p>A function is a block of organized, reusable code that is used to perform a single, related action. Can be called.</p>
<blockquote><p>function myFunction() {</p>
<p>echo &#8220;This is my function!&#8221;;</p>
<p>}</p>
<p>myFunction();</p></blockquote>
<p>These concepts are found in most languages. If you understand what they are and how they work, you are prepared to tackle any coding situation, given that you know the Syntax.</p>
<p>And that leads us to the final step in helping you code faster:</p>
<h3>3. Syntax</h3>
<p>Documentation is your best friend.</p>
<p>You will never outgrow the Documentation of a language.</p>
<p>You will still use Documentation as an expert.</p>
<p>It is your friend. The sooner you make your acquaintance, the faster you will learn.</p>
<p>Why?</p>
<p>Because you now understand pseudocode (logic paraphrased). And you understand the fundamental concepts of coding, all that is left is for you to write it out correctly.</p>
<p><a href="http://php.net/docs.php" target="_blank" rel="noopener">PHP</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference" target="_blank" rel="noopener">JavaScript</a> (though not &#8220;official&#8221;), <a href="https://docs.python.org/3/" target="_blank" rel="noopener">Python</a>, content management systems like <a href="https://codex.wordpress.org/" target="_blank" rel="noopener">WordPress</a>, all have documentation created for you to reference as you write code in that language.</p>
<p>Becoming a good coder happens when you learn to read and benefit from the documentation.</p>
<p>Another benefit of consulting the sources files of a language is that you always get the right answer, not a long list of opinions from a Google search (though Google searches are wonderful).</p>
<h4>Example #1</h4>
<p>Let me give an example of how helpful being able to read documentation is:</p>
<p>Let&#8217;s say I&#8217;m in WordPress and on my blog page I want to have the category show up below the title of every blog post listed. So my loop is showing my latest 6 posts and I want each of their respective categories listed below the post title.</p>
<p>I could go to Google and search for &#8220;how to add the categories to my blog post&#8221; and get an answer that I can copy and paste.</p>
<p><strong>But even better</strong> is to go to the <a href="https://codex.wordpress.org/Function_Reference/get_category" target="_blank" rel="noopener">Codex</a> and get the answer that I need, in addition to all the different uses of the code available.</p>
<p>So in order to do this I need to use WordPress&#8217;s built in function <a href="https://codex.wordpress.org/Function_Reference/get_category" target="_blank" rel="noopener">the_category();</a></p>
<p>As I consult the docs I can glean many things:</p>
<h5>What it does:</h5>
<p>&#8220;Displays a link to the category or categories a post belongs to. This tag must be used within The Loop.&#8221;</p>
<p>Great! This will display a link the the category or categories that I need. AND it works inside the loop, which I need as well.</p>
<h5>Its usage:</h5>
<blockquote><p><?php the_category( $separator, $parents, $post_id ); ?></p></blockquote>
<p>This is the best part. This tells me that there are three built in arguments that I can use with the explanation of each one. Well what if you are not sure how to use them? No prob! For example, lets look at the $separator.</p>
<blockquote><p><?php the_category( &#8216;, &#8216; ); ?></p></blockquote>
<p>This separates each category with a comma and then a space. It also tells us that this separator is a string, this the quotes.</p>
<p>There are also the <a href="https://developer.wordpress.org/reference/functions/the_category/" target="_blank" rel="noopener">WordPress developer docs</a> that give us more info, such as the actual code behind the function. Taking time to look over this will help you learn to code faster.</p>
<h4>Example #2</h4>
<p>Lets look at another example in WordPress: <a href="https://developer.wordpress.org/reference/functions/the_post_thumbnail/" target="_blank" rel="noopener">the_post_thumbnail()</a></p>
<h5>It&#8217;s Use</h5>
<p>Looking at the documentation we see its use:</p>
<p>&#8220;Display the post thumbnail.&#8221;</p>
<h5>It&#8217;s arguments:</h5>
<blockquote><p>the_post_thumbnail( string|array $size = &#8216;post-thumbnail&#8217;, string|array $attr = &#8221; )</p></blockquote>
<p>This tells us it takes two arguments:</p>
<ol>
<li>The size of the image</li>
<li>Attributes that we can define</li>
</ol>
<p>It also gives us a number of examples to help explain including this nifty one:</p>
<blockquote><p>the_post_thumbnail( &#8216;thumbnail&#8217;, array( &#8216;class&#8217; => &#8216;alignleft&#8217; ) );</p></blockquote>
<p>The thumbnail size will be &#8220;thumbnail,&#8221; which is a default WordPress image size and it will assign the image a class of alignleft, which will align it left.</p>
<p>These attributes can be combined as an array and passed as an argument:</p>
<blockquote><p>$attr = array(<br />
&#8216;src&#8217; => $src,<br />
&#8216;class&#8217; => &#8220;your-css-class&#8221;,<br />
&#8216;alt&#8217; => &#8220;your alt text&#8221;<br />
);</p></blockquote>
<p>There are also a handful of examples that explain how this function can be implemented in a more advanced situation. .</p>
<p>You not only get all of the syntax info well defined, but you get practical examples.</p>
<p>So hopefully you see that there is no substitute from the source documentation. Google search will help you find the right documentation and help you immensely, but a habit of checking the documentation will no doubt help you become a better coder and untimaltely helping you learn to code fast and with better accuracy.</p>
<h3>Conclusion</h3>
<p>So in retrospect, these are three concepts that I think can help any CodeNewbie learn to code faster. If I would have grasped these concepts sooner, no doubt I would have wasted less time.</p>
<p>I hope these will help you do the same.</p>
<p><strong>Looking back on your coding journey, what are the things that boosted you forward helping you learn to code faster, and what were the things that held you up? Let&#8217;s discuss!</strong></p>
<p>&nbsp;</p>



