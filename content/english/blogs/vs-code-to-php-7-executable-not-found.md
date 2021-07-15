---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2018-06-01T09:29:24Z
description:  ""
draft:  false
images: 
  -  "/images/2019/12/vs-code-to-php-7-featured.jpg"
slug:  "vs-code-to-php-7-executable-not-found"
tags:  ["Coding Tutorials"]
title:  "Setting VS Code to PHP 7 – Executable Not Found"

---


<p class="textcenter"><img data-rjs="2" src="/images/2019/12/vs-code-to-php-7-featured.jpg" /></p>
<p>After attempting to try out the new <a href="http://php.net/manual/en/migration70.new-features.php#migration70.new-features.null-coalesce-op" target="_blank">null coalescing operator</a> in PHP 7, I realized that my Macbook Pro was still on 5.6. In this post I want to share with you not only how to upgrade your Mac to PHP 7, but how to adjust your PATH to recognize it, and update VS Code to PHP7.&nbsp;</p>
<h2 style="text-align: center;">Setting VS Code to PHP 7</h2>
<h3>1. Upgrade PHP on your Mac</h3>
<p>According to the PHP downloads page, the current stable version at the time of this post is 7.2. If your Mac has on OS of 10.10 or greater, go for it.&nbsp;</p>
<p>Open up your Terminal and type in</p>
<p>curl -s https://php-osx.liip.ch/install.sh | bash -s 7.2</p>
<p>If you prefer an earlier PHP have an OS version before 10.10 then reference <a href="https://php-osx.liip.ch/" target="_blank">this page</a>.</p>
<p>This will install the new version of PHP on your computer.&nbsp;</p>
<h3>2. Adjust your PATH</h3>
<p>After you install the new version of PHP, verify the version by typing in the Terminal:</p>
<p>php -v</p>
<p>Uh, oh. You&#8217;re probably still showing the old version.</p>
<p>Here&#8217;s the deal:</p>
<p><em>php-osx doesn&#8217;t overwrite the php binaries installed by Apple, but installs everything in /usr/local/php5. The new php binary is therefore in /usr/local/php5/bin/php </em>(<a href="https://php-osx.liip.ch/" rel="nofollow" target="_blank">source</a>)</p>
<p>So the PHP binaries installed by Apple are left right where they are, and the new PHP version is installed in a new folder. You need to adjust your PATH to that new location.&nbsp;</p>
<p>You can do so by typing in the Terminal:</p>
<p>export PATH=/usr/local/php5/bin:$PATH</p>
<p>Now check your version again with <em>php -v</em> and you should see the new version.&nbsp;</p>
<h3>3. Update your new location in VS Code</h3>
<p>Now you need to tell Visual Studio Code where your PHP executable is.&nbsp;</p>
<p>On the Mac, &#8220;right-click&#8221; on Finder and choose &#8220;Go To Folder&#8221; and enter&nbsp;</p>
<p>/usr/local/</p>
<p>In the local folder you will see the old PHP5 folder <strong>as well as</strong> the new PHP5 folder which will be something like php5-7.2.2-20180109-122639</p>
<p>If you look in that folder, and then into the bin folder, you will see your new php executable.</p>
<p>This is where we need to point VS code, and we do this in VS Code&#8217;s settings, using &#8220;php.executablePath.&#8221;</p>
<p>So open up your VS Code settings (command + comma) and enter the path to your new executable. So in my example I would put this in my settings.json:</p>
{{< highlight json "style=pygments" >}}
"php.executablePath": "/usr/local/php5-7.2.2-20180109-122639/bin/php"{{< / highlight >}}
<p>And there you go, setting VS Code to PHP 7!</p>



