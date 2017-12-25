+++
categories = ["docker", "ubuntu"]
date = "2016-03-27T13:56:59Z"
title = "DOCKER_OPTS not working in ubuntu 16.04"

+++
In ubuntu 16.04 docker was not loading the ```DOCKER_OPTS``` from ```/etc/default/docker``` file, so I was not able to change DNS of docker
global.


After search a bit i found that [issue ](https://github.com/docker/docker/issues/9889#issuecomment-109766580) with a explanation of why it was
not working.

So basically the systemd docker configuration (```/lib/systemd/system/docker.service```) is not using the ```/etc/default/docker```, the problem is solved by adding an ```EnvironmentFile``` directive and modify command to include the options from file:

```
EnvironmentFile=-/etc/default/docker
ExecStart=/usr/bin/docker daemon $DOCKER_OPTS -H fd://
```
<br />
In the end ```/lib/systemd/system/docker.service``` looks like:

{{< highlight bash >}}
[Unit]
Description=Docker Application Container Engine
Documentation=https://docs.docker.com
After=network.target docker.socket
Requires=docker.socket

[Service]
Type=notify
EnvironmentFile=-/etc/default/docker
ExecStart=/usr/bin/dockerd $DOCKER_OPTS -H fd://
MountFlags=slave
LimitNOFILE=1048576
LimitNPROC=1048576
LimitCORE=infinity
TimeoutStartSec=0

[Install]
WantedBy=multi-user.target
{{</highlight>}}

Once edited, I have saved and restarted the docker service, and voila DOCKER_OPTS was working and my docker images are getting the right DNS.
