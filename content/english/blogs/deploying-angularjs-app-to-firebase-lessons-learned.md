---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2017-02-08T15:45:55Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/angularjs-to-firebase.png"
slug:  "deploying-angularjs-app-to-firebase-lessons-learned"
tags:  ["Coding Tutorials"]
title:  "Deploying An AngularJS App To Firebase - Lessons Learned"

---


<p>After using the Firebase database on a recent AngularJS Project, I decided I wanted to use this service to deploy my apps instead of <a href="http://netlify.com">Netlify</a>.</p>
<p>The <a href="https://firebase.google.com/docs/hosting/deploying">documentation</a> was pretty straightforward:</p>
<ul>
<li>Install Node.js</li>
<li>Install the Firebase CLI using npm</li>
<li>Login to your firebase account</li>
<li>Initialize firebase in project root folder</li>
<li>Choose your settings</li>
<li>Deploy!</li>
</ul>
<p><em>Voila.</em></p>
<p>Unfortunately a couple hours later I was still scratching my head.</p>
<p>Thus, here are a few lessons learned and how hopefully they can help you if you are also using it for the first time and especially if you are deploying an AngularJS app to Firebase.</p>
<h3><strong>Scenario 1: Your deploy is complete and you visit the URL and get this:</strong></h3>
<p class="textcenter"><img src="/images/2019/12/firebase-notification.png" alt=""/></p>
<p>Here is the issue:</p>
<p>There is a prompt in the firebase init that asks: <em>What do you want to use as your public directory?</em> Choosing “public” because it is default is not really a good idea. You MUST choose the folder where your index.html is found. In many apps this is the root folder. In my case, with AngularJS, the index.html is not in the root directory. Where is it? Lets look at Scenario 2.</p>
<h3><strong>Scenario 2: Because it is AngularJS</strong></h3>
<p>When you run firebase init, choose your ‘dist’ folder as this is where your website is “built.” It also contains index.html. Note: On next prompt DO NOT overwrite index.html. Also choose Yes to single page app. After firebase init runs, make sure to run ‘grunt build’ in the Terminal before running ‘firebase deploy’ in order to update the build.</p>
<h3><strong>Scenario 3: Google font errors, Ionicons not showing</strong></h3>
<p>Next up, I had errors with Google fonts as well as my Ionicons. In the Chrome dev tools you can troubleshoot this by looking in the Network tab to see what is not running. Also you can see in Console that Google fonts and Ionicons are using http and Firebase is asking for https. Why? Who knows. Answer &#8211; change http to https in your head source files. Now re-deploy.</p>
<h3><strong>Conclusion</strong></h3>
<p>More may be added to this list as I send more to Firebase. Stay tuned!</p>



