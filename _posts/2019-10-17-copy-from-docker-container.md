---
layout: post
title: "Copy contents from Docker container"
date: 2019-10-17
---

Writing down simple command to copy files from stopped docker containers if you are not used volume mapping.

Run ```docker ps -a```to list the active/inactive containers


<img src="/img/dock1.png" width="1240" height=13>


Run following command to copy the desired content to host machine.

```docker cp <CONTAINER_ID>:<LOCATION OF FILE INSIDE THE CONTAINER>/<FILE_NAME> <HOST_PATH_TARGET>```


<img src="/img/dock2.png">
