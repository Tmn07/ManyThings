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