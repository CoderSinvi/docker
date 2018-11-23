
ubuntu16.04-jira-core
=============


This repository contains the sources for the following [idoall/ubuntu:16.04](https://hub.docker.com/r/idoall/ubuntu/) base images:
- [`ubuntu16.04-jira-core:7.12.3`(*7.12.3-ce.0/Dockerfile*)](https://github.com/idoall/docker/blob/master/ubuntu16.04-jira-core/7.12.3/Dockerfile)



# 相关文章
[Docker 创建 Jira Core/SoftWare 7.12.3 中文破解版](https://mshk.top/2018/11/docker-jira-core-software-7-12-3/)

## Developing

```bash
# Pull image
git clone https://github.com/idoall/docker.git
cd ubuntu16.04-jira/7.12.3

# hack hack hack

# Build
docker build -t idoall/ubuntu16.04-jira-core:<tag> .

# Run rm
docker run -it --name=idoall_jira_core --rm -p 80:8080 idoall/ubuntu16.04-jira-core:<tag> /bin/bash

# After running, wait for 1 minutes.
# Open http://localhost/ in your browser
docker run -d --name=idoall_jira_core -p 80:8080 idoall/ubuntu16.04-jira-core:<tag>

# access the contain
docker exec -it idoall_jira_core /bin/bash
```
# Using docker stack deploy service to create APP



When deploying, pay attention to modifying the  `my.ini` in the `docker-compose.yml` file content.



## deploy service

```bash
docker stack deploy -c <tag>/docker-compose.yml mshk_jira_core
```

## remove deploy

```bash
docker stack rm mshk_jira_core
```

## view service list

```bash
# 所有服务列表
docker service ls

# 指定应用的列表
docker stack services mshk_jira_core
```

## View service status

```bash
watch docker service ps mshk_jira_core
```