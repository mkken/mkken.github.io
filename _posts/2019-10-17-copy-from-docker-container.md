---
layout: post
title: "Copy contents from Docker container"
date: 2019-10-17
---

Writing down simple command to copy files from stopped docker containers if you are not used volume mapping.

Run **docker ps -a** to list the active/inactive containers
![image alt <](/img/dock1.png =100X20)

Run following command to copy the desired content to host machine.

docker cp <CONTAINER_ID>:<LOCATION OF FILE INSIDE THE CONTAINER>/<FILE_NAME> <HOST_PATH_TARGET>
![image alt <](/img/dock2.png =100X20)
