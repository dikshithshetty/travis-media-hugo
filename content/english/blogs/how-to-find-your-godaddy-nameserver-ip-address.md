---
author: "Travis Rodgers"
categories: ["Digital Strategy", "unique"]
date:  2020-01-02T11:41:45Z
description:  ""
draft:  false
images: 
  -  "/images/2020/01/godaddy-nameserver-ip-address-featured.jpg"
slug:  "how-to-find-your-godaddy-nameserver-ip-address"
tags:  ["Digital Strategy", "unique"]
title:  "How to Find a GoDaddy Nameserver IP Address For Any Host"

---


<div class="lead-paragraph"><span class="dropcap">W</span>hen setting custom Nameservers for GoDaddy domains, an IP Address is required for each. In this article, I'll show you how to easily locate that IP Address.</div>
<hr class="lead-hr">

I recently moved my blog to Digital Ocean. My domain is with GoDaddy and when changing the Nameservers over to the three required by Digital Ocean, I was asked for the IP address of each one.

I tried to leave it blank, but the GoDaddy nameserver IP address was a required field.

I wasn't provided with any and couldn't seem to locate any.

If you are in the same boat, just do the following if you are on a Mac or have access to a Linux terminal.

Simply ping the nameserver and it will give you the IP address of it.

{{< highlight bash "style=pygments" >}}ping ns1.digitalocean.com{{< / highlight >}}

And there it is:

<p class="textcenter"><img src="/images/2020/01/godaddy-nameserver-ip-address.png" /></p>

And do the same for the other two nameservers or whatever nameservers you need to point to.



