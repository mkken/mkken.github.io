---
layout: post
title: "Copy contents from Docker container"
date: 2019-10-17
---

Writing down simple command to copy files from stopped docker containers if you are not used volume mapping.

Run <span style="color:blue">docker ps -a</span> to list the active/inactive containers


<img src="/img/dock1.png">


Run following command to copy the desired content to host machine.

<span style="color:blue">docker cp \<CONTAINER_ID>:\<LOCATION OF FILE INSIDE THE CONTAINER>/\<FILE_NAME> \<HOST_PATH_TARGET></span>

<img src="/img/dock2.png">
