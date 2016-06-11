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

## 入门指令
- `docker version` // 版本信息
- `docker search xxxx` // 搜索镜像
- `docker pull dl.dockerpool.com:5000/ubuntu:12.04` // 下载镜像
- `sudo docker run hello-world` // 运行helloxx的镜像，没有的话，pull一个？
- `sudo docker save -o /home/tmn07/hello_docker.tar dl.dockerpool.com:5000/ubuntu` // 将某镜像保存下来。可以用image_id代替镜像名。。


## 火炬
- [大神的博客](https://www.huangwenchao.com.cn/2016/01/learn-docker-1.html)//挺不错的
- [入门教程](http://www.docker.org.cn/book/docker/what-is-docker-16.html)
- [一点内容](http://www.cnblogs.com/fengzheng/p/4958571.html)



