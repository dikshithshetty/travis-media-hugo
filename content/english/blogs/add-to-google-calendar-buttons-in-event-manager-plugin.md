---
author: "Travis Rodgers"
categories: ["Digital Strategy"]
date:  2017-09-08T09:59:08Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/add-to-google-calendar-buttons-in-event-manager-plugin.jpg"
slug:  "add-to-google-calendar-buttons-in-event-manager-plugin"
tags:  ["Digital Strategy"]
title:  "Add To Google Calendar Buttons In Event Manager Plugin"

---


<p>I had a client using Marcus Sykes&#8217;s Event Manager Plugin and they wanted the ability to add the events to their Google Calendar from within WordPress. Not only that, but for anyone visiting their site to be able to add it to their own Google Calendar.</p>
<p>Looking at the <a href="https://wordpress.org/plugins/events-manager/" target="_blank" rel="noopener">advertised Main Features</a> of the plugin, I noticed a bullet point that says:</p>
<ul>
<li>Add to Google Calendar buttons</li>
</ul>
<p>Perfect! Should be easy.</p>
<p>Twenty minutes later, I still had not found this functionality. Normally with a plugin its easy&#8230;.usually just an option to check or a button to click to add it. However, this plugin takes a bit of a different approach.</p>
<p>So in this brief tutorial, I want to show you how to do this (which implies that I eventually found it, right!!??)</p>
<h3>My Example</h3>
<p>Here is the event example that I will use to demonstrate, a single event page for an upcoming 5K Fundraiser:</p>
<p class="textcenter"><img src="/images/2019/12/add-to-google-calendar-buttons-in-event-manager-5.jpg" /></p>
<p>We are going to add the Google Calendar button under the 9:00 am &#8211; 12:30 text.</p>
<h3>Insert Add to Google Calendar buttons in Event Manager Plugin</h3>
<p>So here is how to do it:</p>
<h4>1. In your WordPress Dashboard, in the list on the left, go to Events &#8211;> Settings.</h4>
<p class="textcenter"><img src="/images/2019/12/add-to-google-calendar-buttons-in-event-manager-7.jpg"/></p>
<h4>2. Choose the Formatting Tab and then the Events section</h4>
<p class="textcenter"><img src="/images/2019/12/add-to-google-calendar-buttons-in-event-manager-1.jpg" /></p>
<h4>3. Scroll down to the Single Events Page box.</h4>
<p>Since we are adding this Add To Google Calendar button to our individual event pages, we will use this option (instead of the actual Events page that lists all events).</p>
<p>Now in your WordPress dashboard, in the menu on the left, if you go to Events &#8211;> Help, then you will see all of the Placeholder Codes. There are lots of options here. You can use these to add a vast range of data to your events.</p>
<p>If we scroll down the Placeholder codes in the Help screen, we will find the Placeholder we want to enter in order to add the Add To Google Calendar button:</p>
<p class="textcenter"><img src="/images/2019/12/add-to-google-calendar-buttons-in-event-manager-3.jpg" /></p>
<p>We want to choose the #_EVENTGCALLINK placeholder and add it to our Single Events Page Format</p>
<h4>4. Add this to our Single Events Page Format box</h4>
<p>So back to our Single Events Page format box. In this box you will recognize the placeholders. Just compare them with your Single Event Page and you will see that what is actually displayed is first determined here.</p>
<p>So lets say I want to add it below my Event Time. I would simply go below this section and add:</p>
<div><div>#_EVENTGCALLINK</div></div>
<div></div>
<div></div>
<div class="textcenter"><img src="/images/2019/12/add-to-google-calendar-buttons-in-event-manager-4.jpg" /></div>
<h4>5. Save your settings and go back to your Single Event Page, and there it is!!</h4>
<p class="textcenter"><img src="/images/2019/12/add-to-google-calendar-buttons-in-event-manager-6.jpg" /></p>
<p>You can now click it to add to whatever Google Calendar you are logged into.</p>
<p>And that is simply how to add the Add To Google Calendar Buttons In Event Manager Plugin.</p>



