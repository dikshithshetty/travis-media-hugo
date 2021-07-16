---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2020-01-10T21:31:07Z
description:  ""
draft:  false
images: 
  -  "/images/2020/01/uptime-monitor-for-ghost.jpg"
slug:  "create-uptime-monitor-for-ghost"
tags:  ["Coding Tutorials"]
title:  "How to Create An Uptime Monitor  For Ghost"

---


<div class="lead-paragraph"><span class="dropcap">I</span>t's very important that you know if your site goes down. In this post, I'll show you how to create an uptime monitor for Ghost (or any other service). </div>
<hr class="lead-hr">

I'm happy to be hosting my site with <a href="/recommends/do" target="_blank">Digital Ocean</a> and am also glad they provide alerts for metrics such as CPU usage, Bandwidth, Disk Utilization, etc. 

However, when it comes to receiving alerts when your site goes down you usually have to move into some sort of paid solution, mainly because it seems over-technical or perhaps a hassle to do it ourselves. 

But we're developers right?

And it's actually pretty easy to set up. 

Here's how.

## How To Create An Uptime Monitor For Ghost

First off, I want to give credit for this script to Adam Robertson. He created the script. You can find him on Github as [sierracircle ](https://github.com/sierracircle)and [here is the repo](https://github.com/sierracircle). All I did was tweak it for my own usage because that is what we developers do. 

Now this can really be set up for any service or really any platform that utilizes Linux (Ubuntu specifically). However, I had to make a few adjustments for Ghost so wanted to use it as the example. 

Here's the logic of it:

1. Check every minute to see if a service or services are running.
2. If not, then try to restart it.
3. If it restarts successfully, then it will email you what happened.
4. If it is not able to restart successfully, then it will email you about it. 

That's it. Let's break it down. 

### 1. Install the script

Create the file in the /usr/local/bin folder

{{< highlight shell "style=pygments" >}}sudo nano /usr/local/bin/restart-service{{< / highlight >}}

...and [paste in this code](https://raw.githubusercontent.com/sierracircle/services-checker/master/restart-services). 

### 2. Make some tweaks

First, add in the email address you want to be alerted at in the EMAIL variable at the top. 

{{< highlight shell "style=pygments" >}}##set your email address 
EMAIL="youremail@example.com"{{< / highlight >}}

Second, add in the services you want to check. Options could be 'mysql' 'nginx' 'cron' 'ghost' etc.

Since we are focusing in on Ghost, let's be sure to include 'ghost' as a service. 

But here's the issue: It checks for the 'ghost' service, but if it doesn't detect it and needs to restart it (see line 31), then it actually needs to say ```service ghost_(sitename) start```, not ```service ghost start```. 

If you are unsure what the command is, then run ```ghost restart``` and see what command the terminal shows. In my case it's ```ghost_travis-media```.

Since the service and the restart command are different, we need to account for it by updating that start command. If the service is 'ghost' then it will run that particular start. If any other service, then it will run as normal:

{{< highlight shell "style=pygments" >}}##TRY TO RESTART THAT SERVICE###
  if [[ $i == "ghost" ]]
   then
    service ghost_travis-media start
   else
    service $i start
  fi{{< / highlight >}}

Once that is in place, you are good. Almost...

The other issue I found with the script is that when it detects that the service is down and runs the command to restart, it doesn't allow any time before it checks again. 

So it starts the service and immediately checks the status. For Ghost, it takes a couple of seconds to start fully, thus the check failed every time. 

To fix this, I added a 5 second pause between attempting to start the service and checking the status again. So you will <a href="#full-script">see on line 35</a> after our if statement:

{{< highlight shell "style=pygments" >}}sleep 5{{< / highlight >}}

### 3. Permissions

Now, we are not going to be able to run this. When it hits that ```service $i start``` command it will want to prompt us for our password and that won't work in the world of automation. 

There are a number of different approaches to this. I will give you one solution and that is to allow this specific script to be ran without a password. 

You can do that by editing the ```sudoers``` file (be sure to do this only with nano or vi, not a text editor). So open that for edit:

{{< highlight shell "style=pygments" >}}sudo nano /etc/sudoers{{< / highlight >}}

...and enter as a new line at the bottom (or if your username is already utilizing this service, just add to it):

{{< highlight shell "style=pygments" >}}username ALL=(ALL) NOPASSWD:/usr/local/bin/restart-service{{< / highlight >}}

** **Be sure to replace username with your actual user name. If you are not sure what that is, you can get this by running ```echo $USER``` in the terminal**

Now you can sudo this script and it will run without asking for a password.

### 4. Cron - Checking every minute

Finally, we want to run this script every minute to check the health of our services. 

So let's open the crontab:

{{< highlight shell "style=pygments" >}}sudo nano /etc/crontab{{< / highlight >}}

and enter a new entry at the bottom to run every minute:

{{< highlight shell "style=pygments" >}}* * * * * username sudo /usr/local/bin/restart-service{{< / highlight >}}

** **Again, replace username with your user name**

### 5. Be sure mail is set up

It's a high probability that you do not have the ```mail``` feature set up. It's very easy to do and takes like a minute. 

[Here are the instructions](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-as-a-send-only-smtp-server-on-ubuntu-16-04) on how to install and test that. (And if you do Step 4, then change your email address to ```root``` instead.

### Conclusion

Now you have a script that runs every minute checking for inactive services. If found, then the script will attempt to restart them and email you the outcome. 

<p id="full-script">Full script:</p>

{{< highlight shell "style=pygments" >}}#!/bin/bash
#ver. 4
##this script will check mysql and apache
##if that service is not running
##it will start the service and send an email to you
##if the restart does not work, it sends an email and then exits

##set the path ##this works for Ubuntu 14.04 and 16.04
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

##set your email address
EMAIL="you@example.com"

##list your services you want to check
SERVICES=( 'ghost' 'nginx' 'mysql' 'cron' )

#### OK. STOP EDITING ####

 for i in "${SERVICES[@]}"
  do
 ###CHECK SERVICE####
 `pgrep $i >/dev/null 2>&1`
 STATS=$(echo $?)

 ###IF SERVICE IS NOT RUNNING####
 if [[  $STATS == 1  ]]
  then
  ##TRY TO RESTART THAT SERVICE###
 if [[ $i == "ghost" ]]
  then
   service ghost_travis-media start
  else
   service $i start
 fi
 sleep 5
  ##CHECK IF RESTART WORKED###
  `pgrep $i >/dev/null 2>&1`
  RESTART=$(echo $?)
  if [[  $RESTART == 0  ]]
   ##IF SERVICE HAS BEEN RESTARTED###
   then
    ##REMOVE THE TMP FILE IF EXISTS###
    if [ -f "/tmp/$i" ];
    then
     rm /tmp/$i
    fi

    ##SEND AN EMAIL###
    MESSAGE="$i was down, but I was able to restart it on $(hostname) $(date)  "
    SUBJECT="$i was down -but restarted-  on $(hostname) $(date) "
    echo $MESSAGE | mail -s "$SUBJECT" "$EMAIL"

   else
    ##IF RESTART DID NOT WORK###

    ##CHECK IF THERE IS NOT A TMP FILE###
    if [ ! -f "/tmp/$i" ]; then

     ##CREATE A TMP FILE###
     touch /tmp/$i

     ##SEND A DIFFERENT EMAIL###
     MESSAGE="$i is down on $(hostname)  at $(date)  "
     SUBJECT=" $i  down on $(hostname) $(date) "
     echo $MESSAGE  " I tried to restart it, but it did not work"  | mail -s "$SUBJECT" "$EMAIL"
    fi
  fi
 fi



  done
exit 0;
{{< / highlight >}}



