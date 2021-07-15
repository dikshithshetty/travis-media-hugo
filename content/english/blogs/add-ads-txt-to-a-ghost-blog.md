---
author: "Travis Rodgers"
categories: ["Digital Strategy", "unique"]
date:  2020-01-03T12:11:02Z
description:  ""
draft:  false
images: 
  -  "/images/2020/01/add-ads-txt-to-ghost-blog.jpg"
slug:  "add-ads-txt-to-a-ghost-blog"
tags:  ["Digital Strategy", "unique"]
title:  "How To Add Ads.txt To a Ghost Blog, Self-Hosted"

---


<div class="lead-paragraph"><span class="dropcap">I</span>f you are looking to add an ads.txt to a Ghost Blog on platforms such as Digital Ocean, there are few minor adjustments you must make. I'll show you how to do it in this tutorial. </div>
<hr class="lead-hr">

### What is an Ads.txt file?
According to the [docs](https://support.google.com/adsense/answer/7532444?hl=en), its an initiative to help ensure that your digital ad inventory is only sold through sellers who you've identified as authorized (such as Adsense). Creating this file gives you more control over who is allowed to sell ads on your site and prevent counterfiet inventory from being shown to advertisers. Blah, blah, blah.

For you and me, its a file that companies like Adsense tells us (evens warns us) that we should add to the root of our site. 

And conveniently, they give us the file, packaged and ready to go. 

## How to add Ads.txt to a Ghost blog (self-hosted)
So you want to add this file to the root of your Ghost blog. 

And for sake of example, lets assume you're hosting on Digital Ocean (or really any self-hosted, Ubuntu/Nginx combo). 

Well, when you do so you get a nice 404 page.

<p class="textcenter"><img src="/images/2020/01/add-ads.txt-to-ghost-blog-404-page.png" /></p>

What we actually have to do is allow Nginx to serve static files (or in this case, a static file). 

So SSH into your droplet, or use something like <a href="https://cyberduck.io/" target="_blank">Cyberduck</a> or <a href="https://filezilla-project.org/" target="_blank">Filezilla</a> to SFTP (or if on Windows, the lovely <a href="https://mobaxterm.mobatek.net/" target="_blank">MobaXterm</a>. 

Then navigate over to the ```/etc/nginx/sites-enabled``` folder. There you will see a .conf file for your site. In my case it's **travis.media.conf**.

Open that up with either nano or just download the file from your SFTP connection and view it nicely in VS Code.

Either way, you will see some location blocks. 

Under those, create a new location for your ads.txt file by adding:

{{< highlight "style=pygments" >}}location ~ ^/ads.txt {
  root /var/www;
}{{< / highlight >}}

Then place your ads.txt file into the /var/www folder. 

Clear your cache (or try a diff browserr) and you will see that you can now access your ads.txt file from the browser, meaning Google can detect it. [Here's mine](/ads.txt). 
<hr>

### Bonus: How to serve static files in Ghost

In addition to the above, this is how you can serve any static file in Ghost. 

In fact, you may want to just create a static folder by which you can serve things like PDFs, CVs, downloadables, etc. from your website. 

To do so, add a new location block in that .conf file like so:

{{< highlight "style=pygments" >}}location /static/ {
    alias /var/www/static/;
}{{< / highlight >}}

In doing this, you can now add any asset to the /var/www/static directory and serve it after the /static/ url like ```travis.media/static/resume.pdf``` or ```travis.media/static/free-cheat-sheet.pdf```.

### Conclusion
So that's how you add ads.txt to a Ghost blog and really how you can serve a single or entire directory of static files to your audience.



