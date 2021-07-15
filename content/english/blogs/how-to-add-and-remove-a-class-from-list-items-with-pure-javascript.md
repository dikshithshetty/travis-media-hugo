---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-08-13T09:57:20Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/add-and-remove-a-class-from-list-items-with-javascript.jpg"
slug:  "how-to-add-and-remove-a-class-from-list-items-with-pure-javascript"
tags:  ["Coding Tutorials"]
title:  "How to Add and Remove a Class From List Items With Pure JavaScript"

---


<p>In this post I&#8217;ll show you an easy block of code by which you can add and remove a class from list items, not with jQuery, but with pure JavaScript.</p>
<p>Lately, I&#8217;ve been trying to write more JavaScript over jQuery. I have no dislike of jQuery and actually use it often, however, it is very, very easy to become reliant on it.</p>
<p>I was recently working on a project where we had a row of buttons. Clicking a button generated a new view via Ajax with some different functionalities. I was asked to make each of the buttons highlight when clicked, only one button at a time being highlighted.</p>
<p>Normally I would do this with jQuery&#8217;s addClass/removeClass, but I thought I should sharpen my vanilla JavaScript and opted to do it that way.</p>
<p>It&#8217;s pretty simple, here are the results. <strong>Just click on the buttons and see.</strong></p>
<style><span data-mce-type="bookmark" style="display: inline-block; width: 0px; overflow: hidden; line-height: 0;" class="mce_SELRES_start">﻿</span>div#button-row{text-align:center;}#button-row li {list-style-type: none;}.post-button button {text-align: center;height: 100px;color: black;border: 4px solid black;background-color: #f3f3f3;border-radius: 10px; padding: 2px 10px;}.menuActive {box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.05) inset, 0 0 15px #0d6adc;}</style>
<div id="button-row" style="height: 100px;">
<ul>
<li class="grid-33 first post-button"><button>Btn 1</button></li>
<li class="grid-33 post-button"><button>Btn 2</button></li>
<li class="grid-33 post-button"><button>Btn 3</button></li>
</ul>
</div>
<p class="clear"></p>
<p>As you click on a button, a menuActive class is added to that button. When you click on another button, the menuActive class is removed from all buttons and added to the new button clicked. The menuActive class gives a blue box shadow to the button.</p>
<p>Neat effect, eh?</p>
<p>So in my example here is the simple HTML:</p>
{{< highlight markdown "style=pygments" >}}<div id="button-row">
  <ul>
    <li class="one-third first post-button"><button>Button 1</button></li>
    <li class="one-third post-button"><button>Button 2</button></li>
    <li class="one-third post-button"><button>Button 3</button></li>
  </ul>
</div>{{< / highlight >}}
<p>Next, the CSS:</p>
{{< highlight css "style=pygments" >}}div#button-row {
  text-align:center;
}

#button-row li {
  list-style-type: none;
}

.post-button button {
  text-align: center;
  height: 100px;
  color: black;
  border: 4px solid black;
  background-color: #f3f3f3;
  border-radius: 10px;
  padding: 2px 10px;
}

.menuActive {
  box-shadow: 0px 1px 3px rgba(0, 0, 0, 0.05) inset, 0 0 15px #0d6adc;
}{{< / highlight >}}
<p>And here is the JavaScript:</p>
{{< highlight javascript "style=pygments" >}}
var btnContainer = document.getElementById("button-row");
var btns = btnContainer.getElementsByTagName("button");
for (var i = 0; i < btns.length; i++) {
  btns[i].addEventListener("click", function() {
    (document.querySelector('.menuActive')) ? document.querySelector('.menuActive').classList.remove('menuActive') : '';
    this.classList.add('menuActive');
  });
} 
{{< / highlight >}}
<p>A simple &#8220;for loop&#8221; looping through the buttons. An event listener is set up for the click. When a button is clicked, menuActive is first removed from ALL of them, then it is added to the clicked button.</p>
<p>When another button is clicked, menuActive is again first removed from ALL of them, and then added to the clicked button.</p>
<p>No jQuery needed.</p>



