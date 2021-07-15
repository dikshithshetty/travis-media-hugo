---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-09-04T22:45:25Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/javascript-reduce-method.jpg"
slug:  "understanding-the-javascript-reduce-method"
tags:  ["Coding Tutorials"]
title:  "Understanding the JavaScript Reduce Method"

---

<p>One of the hardest JavaScript methods to grasp is the <strong>reduce</strong>&nbsp;method, yet it is very powerful. In this post, I&#8217;ll break it down for you step-by-step.</p>
<h2>What is the JavaScript reduce method?</h2>
<p><strong><em>The reduce() method loops through an array, executing a function for each value of the array, from left to right, and reduces the array to a single value.</em></strong></p>
<p>Breaking it down it&#8230;</p>
<ul>
<li>loops through an array</li>
<li>executes a function for each element of the array</li>
<li>and reduces the array to a single value</li>
</ul>
<p>To better understand this let&#8217;s just walk through the syntax step by step. Let&#8217;s build out an empty function to demonstrate.</p>
<p>Let&#8217;s say we have an array called arrayExample. Let&#8217;s <strong>first</strong> attach our method to it.</p>
{{< highlight javascript "style=pygments" >}}arrayExample.reduce(){{< / highlight >}}
<p>&nbsp;</p>
<p><strong>Second</strong>, let&#8217;s enter a callback function. This is the function that will be executed on every element as it loops through an array:</p>
{{< highlight javascript "style=pygments" >}}arrayExample.reduce(function(){

}){{< / highlight >}}
<p><strong>Third</strong>, let&#8217;s talk about the reduce method parameters as this is what trips everyone up: The callback function has four parameters:</p>
<p>1. <em>accumulator</em> &#8211; accumulates all of the callbacks&#8217; returned values (<strong>required</strong>).<br />
2. <em>element</em> &#8211; value of the current element (<strong>required</strong>)<br />
3. <em>index</em> &#8211; index of the current element (<em>optional</em>)<br />
4. <em>arr</em> &#8211; the original array object (<em>optional</em>)</p>
<p>The element is simply the array element as it loops through each time. Index is&#8230;.well the index. Arr is the array object, and I have no clue the value of this array object.</p>
<p><strong>But what is this accumulator?</strong></p>
<p>Well, think about this: If we are calling a function on each element, and these elements will be reduced into one single value, there needs to be a specified value where the accumulation happens, a value that totals up the changes into a single value. This is the accumulator!!</p>
<p>You will often see this called &#8216;total&#8217; or &#8216;acc&#8217;. Let&#8217;s use acc in our examples.</p>
<p>So let&#8217;s tally it up to the final syntax:</p>
{{< highlight javascript "style=pygments" >}}arrayExample.reduce(function(acc, element, index, arr){

}){{< / highlight >}}
<h3>Example 1</h3>
<p>Let&#8217;s try out a simple example to start:</p>
<p><strong>Let&#8217;s take an array, and reduce the elements into one final sum.</strong></p>
<p>Open up the console below and type an array such as:</p>
    {{< highlight javascript "style=pygments" >}}var numbers = [0, 1, 2, 3, 4, 5, 6];{{< / highlight >}}
<p>So whenever I work with the reduce method (as well as forEach, filter, and map), I always use this four step method to build out the method:</p>
<p><strong>First,</strong> add the method to the end of our array:</p>
    {{< highlight javascript "style=pygments" >}}numbers.reduce();{{< / highlight >}}
<p>&nbsp;</p>
<p><strong>Second</strong>, add the callback function that will be called on each element. (You can also call an already pre-defined function instead of a callback)</p>
{{< highlight javascript "style=pygments" >}}numbers.reduce(function(){

}){{< / highlight >}}
<p><strong>Third</strong>, we will enter our accumulator (required) and our current element (required) as arguments:</p>
{{< highlight javascript "style=pygments" >}}numbers.reduce(function(acc, element){

}){{< / highlight >}}
<p><strong>Finally</strong>, we will enter a condition into our function that adds the elements.</p>
{{< highlight javascript "style=pygments" >}}numbers.reduce(function(acc, element){
  return acc + element;
}){{< / highlight >}}
<p>And we get 21!</p>
<p>Great!</p>
<p>Now here is what it is doing, broken down:</p>
<p class="textcenter"><img src="/images/2019/12/reduce-method-broken-down.png" alt="reduce method broken down" /></p>
<h3>One More Parameter</h3>
<p>Now there is ONE MORE parameter and it&#8217;s called:</p>
<p>initialValue;</p>
<p>So in total we have:</p>
{{< highlight javascript "style=pygments" >}}arrayExample.reduce(function(acc, element, index, arr){ 

}, initialValue){{< / highlight >}}
<p>&nbsp;</p>
<p><strong>And simply put, the initialValue is the value by which the accumulator will start on. Let&#8217;s try an example using the initialValue:</strong></p>
<p>Let&#8217;s take a look at the same example as above, but using an initialValue.</p>
<h3>Example 2</h3>
<p>So based on our example above, here is our array again:</p>
    {{< highlight javascript "style=pygments" >}}var numbers = [0, 1, 2, 3, 4, 5, 6];{{< / highlight >}}
<p>&nbsp;</p>
<p>&#8230;and here is our reduce function with the initialValue of 8:</p>
{{< highlight javascript "style=pygments" >}}numbers.reduce(function(acc, element){
  return acc + element;
}, 8){{< / highlight >}}
<p>Now what this does, is it starts the accumulator at 8, giving us a return value of 29. Here is the breakdown showing the difference. See how the accumulator begins with 8?:</p>
<p class="textcenter"><img src="/images/2019/12/reduce-method-broken-down-initialvalue.png" alt="reduce-method-broken-down-initialvalue" /></p>
<p><strong>*** If there is no initialValue provided, the accumulator starts as the value of the first array element.</strong></p>
<p>If there is an initialValue, this will be the initial value of the accumulator from the start. Okay, not too bad.</p>
<h3>Example 3</h3>
<p>Let&#8217;s look at a final example to assure that we understand the basics of reduce().</p>
<p>Let&#8217;s look at some data (State and Population):</p>
{{< highlight php "style=pygments" >}}
var population = [
  {
    state: 'California',
    pop: 39780000,
  },
  {
    state: 'Virginia',
    pop: 8412000,
  },
  {
    state: 'Florida',
    pop: 20610000,
  },
  {
    state: 'Maine',
    pop: 1331000,
  },
]{{< / highlight >}}
<p><strong>Let&#8217;s use the reduce() method to get the total population of our four states.</strong></p>
<p>Why don&#8217;t you give it a shot? Add up the populations (using element.pop) using reduce().</p>
<p>See the answer below.</p>
<p>Ok, so let&#8217;s follow the 4-step process again:</p>
<p><strong>First</strong>, we&#8217;ll attach the reduce() method:</p>
{{< highlight javascript "style=pygments" >}}population.reduce(){{< / highlight >}}
<p>&nbsp;</p>
<p><strong>Second,</strong> our callback function:</p>
{{< highlight javascript "style=pygments" >}}population.reduce(function(){

}){{< / highlight >}}
<p><strong>Third</strong>, our arguments (acc and element are required):</p>
{{< highlight javascript "style=pygments" >}}population.reduce(function(acc, element){ 

}){{< / highlight >}}
<p><strong>Fourth</strong>, our conditions:</p>
{{< highlight javascript "style=pygments" >}}population.reduce(function(acc, element){
  return element.pop + acc;
}){{< / highlight >}}
<h4>Wrong Answer?</h4>
<p>Now what did you get?</p>
<p><em><strong>Did you get 1331000206100008412000?</strong></em></p>
<p>If you did, you are wrong, BUT this is a great thing because the lesson will much more beneficial than the mistake.</p>
<p>You see, <em>if you did not set an initial value, then you actually started off with the number 39780000 initially!!!</em></p>
<p>Instead, we need to start off with an initialValue of 0. So try it with the 0.</p>
{{< highlight javascript "style=pygments" >}}population.reduce(function(acc, element){

  return element.pop + acc;

}, 0){{< / highlight >}}
<p>..and you see that we now get the correct answer of 70133000.</p>
<p>Great work in tackling an initially difficult, but extremely powerful, method.</p>



