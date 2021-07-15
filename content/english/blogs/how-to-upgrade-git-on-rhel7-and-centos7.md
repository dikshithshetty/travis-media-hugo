---
author: "Travis Rodgers"
categories: ["Coding Tutorials"]
date:  2020-05-21T19:31:05Z
description:  ""
draft:  false
images: 
  -  "/images/2020/05/upgrade-git-in-RHEL7-centOS7.jpg"
slug:  "how-to-upgrade-git-on-rhel7-and-centos7"
tags:  ["Coding Tutorials"]
title:  "How to Upgrade Git on RHEL7 and CentOS7"

---


<div class="lead-paragraph"><span class="dropcap">R</span>ed Hat Enterprise Linux 7 (RHEL7) comes with git 1.8. And git 1.8 is old and unusable in most situations. So how you do upgrade it. Well, with this script of course.</div>

<hr class="lead-paragraph">

Create a file:

{{< highlight shell "style=pygments" >}}touch gitupgrade.sh{{< / highlight >}}

And add the following to it:

{{< highlight shell "style=pygments" >}}yum -y remove git
yum -y clean packages
mkdir tempgit
cd tempgit
yum install -y autoconf cpio curl-devel expat-devel gcc gettext-devel make openssl-devel perl-ExtUtils-MakeMaker zlib-devel
wget -O v2.24.1.tar.gz https://github.com/git/git/archive/v2.24.1.tar.gz
tar -xzvf ./v2.24.1.tar.gz
cd git-2.24.1/
make configure
./configure --prefix=/usr/local/git
make && make install
ln -sf /usr/local/git/bin/* /usr/bin/
cd ..
rm -fr git-2.24.1
cd ..
rm -ft tempgit
echo "results"
which git
git --version
{{< / highlight >}}

The run it to upgrade:

```shell
sudo sh gitupgrade.sh
```

And that's a wrap

