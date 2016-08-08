### aliyun配置
- CentOs吧

### linux
- 登入
	- ssh root@42.96.179.94 
- 传文件
	- sudo scp root@42.96.179.94:/var/www/html/bs.pdf /var/local/ 
	> 下载一个文件。 -r 下载整个目录。注意本地目录的写入权限
	- scp /path/filename username@servername:/path   
	- 上传。。-r 目录
- vim 
	- esc模式 :q :w filename
	- 编辑模式。。。


### 搭建node的hexo博客
- yum install nodejs 
> node版本太低。。。
- yum install npm
- 一定要换[npm淘宝源](https://npm.taobao.org/)。。。。

### git远程服务器
- yum install git?
- adduser git //deluser -r git
- passwd git  //设置密码。。ssh配置失败。。
- git init --bare new.git // 现在在/srv 下进行的，生产版本库文件夹？
- chown -R git:git new.git
- 本地上 git clone git@42.96.179.94:/srv/new.git  //需要密码。。
- 禁用shell登录..[git远程服务器搭建](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000#0)

### 小记
- mongod 直接启动。。
	- mongo客户端等，在 /usr/src/mongodb-linux ..
- mysql 在？？？？？/var/lib/mysql
- service httpd
- 还没有配node的服务器 /usr/src/node-v4.4.7-linux-x64/bin 添加带PATH里了，但是找不到是那个文件加的PATH。。
- jdk 在 /usr/lib/jdk.....
- tomcat 在 /usr/local/apache_tocat....
	- /usr/local/apache-tomcat-x/bin/shutdown.sh
	- /usr/local/apache-tomcat-x/bin/startup.sh
- 