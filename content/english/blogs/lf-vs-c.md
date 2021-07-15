---
author: "Travis Rodgers"
date:  2020-05-08T23:26:00Z
description:  ""
draft:  true
slug:  "lf-vs-c"
images: 
  -  "/images/2019/12/get-all-post-tags-alphabetically-indexed-featured.png"
title:  "LF vs CRLF: A Permanent Fix for Windows Users"

---


For repos that were checked out after those global settings were set, everything will be checked out as whatever it is in the repo – hopefully LF (\n). Any CRLF will be converted to just LF on checkin.

{{< highlight shell "style=pygments" >}}
git config --global core.eol lf
git config --global core.autocrlf input
{{< / highlight >}}

With an existing repo that you have already checked out – that has the correct line endings in the repo but not your working copy – you can run the following commands to fix it:
{{< highlight shell "style=pygments" >}}
git rm -rf --cached .
git reset --hard HEAD
{{< / highlight >}}
This will delete (rm) recursively (r) without prompt (-f), all files except those that you have edited (--cached), from the current directory (.). The reset then returns all of those files to a state where they have their true line endings (matching what's in the repo).

https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration

standard_init_linux.go:211: exec user process caused "no such file or directory"



