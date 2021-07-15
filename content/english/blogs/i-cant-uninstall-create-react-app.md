---
author: "Travis Rodgers"
date:  2020-01-27T00:03:21Z
description:  ""
draft:  true
slug:  "i-cant-uninstall-create-react-app"
title:  "Can't Uninstall Create-React-App - \"up to date in...\""
images: 
  -  "/images/2019/12/get-all-post-tags-alphabetically-indexed-featured.png"

---


<div class="lead-paragraph"><span class="dropcap">I</span>f it's been a whille since you've worked with React, you may have an out of date global create-react-app package that needs to be removed. However, doing so may give you trouble. Here's how to get set up again. </div>
<hr class="lead-hr">

If it's been a little time since you've worked with React, you may have an out of date global create-react-app package that needs to be removed. However, doing so may give you trouble. Here's how to get set back up.

It had been a while since I had worked with React. My last experience with it began with an ```npx create-react-app my-app``` command to start a new project. 

However, when I ran this command today I got an error stating:

> A template was not provided. This is likely because you're using an outdated version of create-react-app.
Please note that global installs of create-react-app are no longer supported.

Okay, well last I checked a global install was legit.

So I did a quick Google search and came across the updated documentation stating:

*If you've previously installed ```create-react-app``` globally via ```npm install -g create-react-app```, we recommend you uninstall the package using ```npm uninstall -g create-react-app``` to ensure that ```npx``` always uses the latest version.*

Makes sense. I had installed it globally and now I needed to unistall it.

Surely I can just type:

{{< highlight javascript "style=pygments" >}}npm uninstall -g create-react-app{{< / highlight >}}

But when I did I kept getting the response:

_up to date in 0.031s_

So it wasn't uninstalling.

How do I uninstall this global create-react-app module?

## How to Uninstall Create-React-App
Basically you have three ways to do it:

1. **Try the command above that I mentioned:** ```npm uninstall -g create-react-app``` as it may work for you. If not then... 
2. **Try yarn!!** Yarn is great and you can run the same command by typing ```yarn global remove create-react-app```
3. **A manual removal.** If neither of the above work, which is what happened in my case then try this:

First locate the package by typing in your terminal:
{{< highlight shell "style=pygments" >}}which create-react-app{{< / highlight >}}

You will get an outcome like: ```/usr/local/bin/create-react-app```

That's your path to the package. 
 
Next, remove it with:
{{< highlight shell "style=pygments" >}}rm -rf /usr/local/bin/create-react-app{{< / highlight >}}

And that's it. 

Remember don't install it globally anymore, but install it on a per project basis with:
{{< highlight javascript "style=pygments" >}}npx create-react-app <project_name>{{< / highlight >}}

And that's it!

![pixel-filler](/images/2020/01/pixel-filler.png)

![travis-media-logo-light](/images/2020/01/travis-media-logo-light.png)

![light-mode-icon](/images/2020/01/light-mode-icon.png)

![dark-mode-icon](/images/2020/01/dark-mode-icon.png)



