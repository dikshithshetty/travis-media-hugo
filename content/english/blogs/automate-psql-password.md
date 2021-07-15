---
author: "Travis Rodgers"
categories: ["Coding Tutorials", "unique"]
date:  2020-01-21T12:05:13Z
description:  ""
draft:  false
images: 
  -  "/images/2020/01/automate-psql-password.jpg"
slug:  "automate-psql-password"
tags:  ["Coding Tutorials", "unique"]
title:  "How to automate the psql password"

---


<div class="lead-paragraph"><span class="dropcap">P</span>assword prompts really put a damper on automation. In this post, I want to show you how to automate the psql password so you can run Postgres commands in a scripting environment.</div>
<hr class="lead-hr">

So let's create a script that:

1. Authenticates as the postgres user
2. Creates two databases, two users for those databases, and two passwords
3. Gives a success message upon completion

Here's the script.

{{< highlight shell "style=pygments" >}}#!/bin/bash

#PSQL variables
psqlUser='postgres'
psqlPassword='testpassword'

#DB & User Variables
dbOne=one_db
userOne=one
passwordOne=testpassword

dbTwo=two_db
userTwo=two
passwordTwo=testpassword

RUN_ON_MYDB="psql -X -U $psqlUser password=$psqlPassword --set ON_ERROR_STOP=on"

$RUN_ON_MYDB << PSQL
CREATE DATABASE $dbOne;
CREATE USER $userOne WITH PASSWORD '$passwordOne';
ALTER DATABASE $dbOne OWNER TO $userOne;
grant all privileges on database $dbOne to $userOne;

CREATE DATABASE $dbTwo;
CREATE USER $userTwo WITH PASSWORD '$passwordTwo';
ALTER DATABASE $dbTwo OWNER TO $userTwo;
grant all privileges on database $dbTwo to $userTwo;
PSQL

if [ $? -eq 0 ]; then
    echo "Success! DBs, Users, and PWs created."
else
    echo "Stopped due to an error. Try again."
fi

{{< / highlight >}}

Note that we are able to pass in the ```password=$psqlPassword``` parameter to the psql command and this authenticates the script when it runs.

And that's how to automate the psql password!

