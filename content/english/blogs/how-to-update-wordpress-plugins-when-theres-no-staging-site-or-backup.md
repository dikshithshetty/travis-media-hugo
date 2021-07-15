---
author: "Travis Rodgers"
categories: ["Freelancing Tips", "Digital Strategy"]
date:  2020-07-20T18:29:41Z
description:  ""
draft:  false
images: 
  -  "/images/2020/07/updaate-wordpress-plugins.jpg"
slug:  "how-to-update-wordpress-plugins-when-theres-no-staging-site-or-backup"
tags:  ["Freelancing Tips", "Digital Strategy"]
title:  "How To Safely Update WordPress Plugins When There's No Staging Site"

---


<div class="lead-paragraph"><span class="dropcap">A</span> client asks you to update all their plugins, but there's no staging site to work to assure nothing breaks. How do you properly update their plugins in a safe manner?</div>
<hr class="lead-paragraph">

Years ago I did some contract for an agency out of Colorado. One of their managers asked me one day to update all the plugins on a client's WordPress site. I said, "Cool, is there a staging site I can do this on, and then transfer over the results when I'm done?"

He said, "No. They don't have one."

Okay. So if I update these 20+ plugins and one of them breaks the site, what do we do? What if I get the white screen of death and can't access the admin part of the site?

I was still fairly new to web development at the time, but I still think it's a valid concern.

The process my manager laid out for me is one that I will share with you below. It's a process that I use frequently when there is no staging site.

### How To Safely Update WordPress Plugins When There's No Staging Site

1. First, get FTP or Control Panel access to the client's site. This is crucial because if the site goes down, this assures that you can still access the files to undo the damage.
2. Download the latest versions of all the plugins you wish to update from the [WordPress plugin repository](https://wordpress.org/plugins/). Upload all of these zip files to your plugins folder.
3. Take the first live plugin you wish to update and add the prefix "old_" to the folder name. This disables the plugin (since it has a different name). Then extract the latest zip file (which will be the right folder name and will be automatically activated). Check the site for any issues. Repeat for all plugins.

### A Practical Example

Lets say you are updating the plugin/folder "advanced-custom-fields."

Upload the latest zip file to the plugin folder.

Change the folder name "advanced-custom-fields" to "old_advanced-custom-fields."

Then extract the latest zip file (which adds the new folder as "advanced-custom-fields"). So at this point you have the new plugin ready to go AND the old plugin deactivated with the "old_" prefix. Now go and check your site for issues. If an issue is found or the site crashes, simply delete the plugin and remove the "old_" prefix from the previous version to "rollback."

### Conclusion

Ultimately this allows you to update to the latest version of that plugin while keeping a disabled copy of the old version for easy reversal if things go wrong. If all goes well, simply delete the old version and move on to the next.



