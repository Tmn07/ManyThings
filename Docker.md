# Docker

[TOC]

## 是啥子
- 打包好你的运行环境和代码
- 然后在能运行docker的机子下
- 带上相应的指令
- 即可拥有你的那些环境和代码

## 安装
- `sudo apt install docker`
- `sudo apt install docker.io`

## 概念
- 镜像
- 容器
- 仓库（远程）
	- docker-registry 本地私有仓库——可弄成局域网内的服务～


![cmd](./resource/docker_cmd.png)

## 入门指令
-  docker login
- `docker version` // 版本信息
- `docker search xxxx` // 搜索镜像
- `docker pull dl.dockerpool.com:5000/ubuntu:12.04` // 下载镜像
- `sudo docker run hello-world` // 运行helloxx的镜像，没有的话，pull一个？
	- 	-t:在新容器内指定一个伪终端或终端。-i:允许你对容器内的标准输入 (STDIN) 进行交互。
	- 	-d: 后台运行，返回容器id
	- 	-P:将容器内部使用的网络端口映射到我们使用的主机上。
- 	docker ps 查看正在运行的容器
- 	docker logs [容器id] 查看返回信息
- 	docker commit -m '' -a '' 容器id  xxx/xxx[:xx]
-  `sudo docker save -o /home/tmn07/hello_docker.tar dl.dockerpool.com:5000/ubuntu` // 将某镜像保存下来。可以用image_id代替镜像名。。
-   docker load < xxx //从磁盘导入镜像

- Dockerfile
	- 写下一堆操作脚本。生成新的镜像。
	- docker build -t="xx/xx[:xx]" . // .为当前目录下的Dockerfile.


## 火炬
- [大神的博客](https://www.huangwenchao.com.cn/2016/01/learn-docker-1.html)//挺不错的
- [入门教程](http://www.docker.org.cn/book/docker/what-is-docker-16.html)
- [一点内容](http://www.cnblogs.com/fengzheng/p/4958571.html)



