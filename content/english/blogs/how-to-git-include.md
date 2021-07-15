---
author: "Travis Rodgers"
date:  2020-05-14T02:43:54Z
description:  ""
draft:  true
slug:  "how-to-git-include"
title:  "How to Git Include certain files instead of gitignore"
images: 
  -  "/images/2019/12/get-all-post-tags-alphabetically-indexed-featured.png"

---


Sometimes there is a .gitignore file in a parent directory, but in your child directory you want to override a specific path. Here's how.

And sometimes you want to ignore an entire folder, so you add it. However, there is one particular file you want to not ignore in it.

How do you include it?

Simple, just negate it with a bang.

**Example**

{{< highlight shell "style=pygments" >}}wp-content/*
!wp-content/themes/{{< / highlight >}}

In this example, we are ignoring everything in the wp-content folder, except for the themes folder. We ignore it all, then we include the particular.

That "!" exclamation point negates the ignore. And since it comes after the ignore, it overrides it for that folder.

That's it.



