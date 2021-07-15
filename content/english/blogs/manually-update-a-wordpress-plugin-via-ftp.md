---
author: "Travis Rodgers"
date:  2017-08-31T11:45:41Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/update-a-wordpress-plugin-via-ftp.jpg"
slug:  "manually-update-a-wordpress-plugin-via-ftp"
title:  "How To Manually Update A WordPress Plugin Via FTP"

---


<p>If you normally download WordPress plugins from their <a href="https://wordpress.org/plugins/" target="_blank" rel="noopener">repository</a>, then you are used to updating them within the WordPress dashboard. It&#8217;s as simple as pressing &#8216;Update.&#8217;</p>
<p>Well&#8230;..simple, until one day you do it and your site breaks.</p>
<p>Even worse is doing this on a site that you are maintaining for a client!</p>
<p>In addition, there will be times where you purchase a premium version of a free plugin or purchase a third party plugin, and any updates to these come by way of a zip file.</p>
<p>In either case, you will want to update a WordPress plugin via FTP.</p>
<p>In fact, any time that you want to be certain that you will not compromise a site, downloading the zip file update from the actual company&#8217;s website and manually installing this may be your best bet.</p>
<h2>How To Update A WordPress Plugin Via FTP</h2>
<p>Here&#8217;s how you would do it:</p>
<p style="padding-left: 30px;">1. Download an FTP client. I recommend <a href="https://cyberduck.io/" target="_blank" rel="noopener">Cyberduck</a> or <a href="https://filezilla-project.org/download.php" target="_blank" rel="noopener">FileZilla</a>. They are both free and will do the job well.</p>
<p style="padding-left: 30px;">2. Get your FTP login information from your hosting company. Normally you can go to your cPanel, select the FTP Accounts folder, and down at the bottom you can click &#8220;Configure FTP client.&#8221; This will show you your login data (and often have a FTP configuration file that you can download and open which will connect your FTP client for you!!).</p>
<p style="padding-left: 30px;">3. Once you are logged in go to the wp-content folder (or make sure you are in this folder), and open up the plugins folder.</p>
<p style="padding-left: 30px;">4. Now on your computer (not the FTP client), go back to where you downloaded your updated plugin zip file and double click it to extract it in to a new folder. Rename this folder so that it has the words NEW- in front of it (so if wordpress-seo is the folder, rename it to NEW-wordpress-seo).</p>
<p style="padding-left: 30px;">5. Drag this file into your plugins folder in the FTP client. (Be sure not to drag into another plugin&#8217;s folder, but the actual root folder called plugins.)</p>
<p style="padding-left: 30px;">6. Now in the FTP client, rename the original (current) plugin folder so that it has the words OLD- in front of it (so if wordpress-seo is the folder, rename it to OLD-wordpress-seo.</p>
<p style="padding-left: 60px;">**Now to make sure we are tracking, there will be a NEW- and OLD- version of this plugin in your FTP client. The OLD is the old version and the NEW is the updated version. At this point your plugin is disabled on your site.</p>
<p style="padding-left: 30px;">7. Finally, rename the NEW- version back to its original name by deleting the prefix NEW-.</p>
<p style="padding-left: 60px;">**So in the end you have the live updated plugin folder and the old folder with the OLD- prefix.</p>
<h3>Now Test Your Site</h3>
<p>Now check your site and see that if it is functioning properly after the update. If something goes bonkers, then do the reverse of the above. That is&#8230;.rename the live folder with the NEW- prefix and remove the OLD- from the older version to revert back.</p>
<h3>Conclusion</h3>
<p>So this is how to safely update a WordPress plugin via FTP. It allows you to easily revert back to the old version of the plugin if something breaks, and is a great approach to updating a client&#8217;s site or a third party plugin that provides you with only a zip file.</p>



