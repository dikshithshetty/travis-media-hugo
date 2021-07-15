---
author: "Travis Rodgers"
date:  2020-07-20T21:42:59Z
description:  ""
draft:  true
slug:  "docker-multistage-build-arg-and-env-heres-how-to-persist-between-stages"
title:  "Docker Multistage Build ARG and ENV: Here's How To Persist Between Stages"
images: 
  -  "/images/2019/12/get-all-post-tags-alphabetically-indexed-featured.png"

---


How do you persist arguments between stages in Docker multi-stage builds? In this blog post, I'll explain exactly how to do it.

Persisting ARGs Between Stages

For an ARG to be global, it must be declared before the first FROM statement (or build)

{{< highlight shell "style=pygments" >}}ARG VERSION=3.2
FROM alpine{{< / highlight >}}

Persisting ENVs between Stages

