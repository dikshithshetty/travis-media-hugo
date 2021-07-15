---
author: "Travis Rodgers"
date:  2020-05-11T17:08:43Z
description:  ""
draft:  true
slug:  "how-to-speficy-specific-key-on-git-push"
title:  "How to Speficy Specific Key On Git Push"
images: 
  -  "/images/2019/12/get-all-post-tags-alphabetically-indexed-featured.png"

---




Starting from Git 2.3.0 we also have the simple command (no config file needed):

```sh
GIT_SSH_COMMAND='ssh -i private_key_file' git clone user@host:repo.git
```

