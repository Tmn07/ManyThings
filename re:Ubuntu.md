# Re:从零开始的Ubuntu配置

## qcloud
- ssh ubuntu@123.206.196.117
- 腾讯云会经常断开。。[`packet_write_wait: Connection to 123.206.196.117 port 22: Broken pipe`](http://askubuntu.com/questions/127369/how-to-prevent-write-failed-broken-pipe-on-ssh-connection)。设置一下客户端 /etc/ssh/ssh_config 
```
Host *
ServerAliveInterval 120
```

## LAMP
- [某博客](http://www.linuxeden.com/html/softuse/20140610/152522.html)
- 他说用root就root吧。。
- 先更新一波源


- 发现无法 sudo service apache2 restart .
- 在 /etc/apache2/apache2.conf 里加一句 ServerName localhost:80
- phpmyadmin在/usr/share/phpmyadmin目录，所以就用命令：sudo ln -s /usr/share/phpmyadmin /var/www/html 建立连接。


- sudo service mysql []
- sudo service apache2 []

(13)Permission denied: AH00072: make_sock: could not bind to address [::]:80
(13)Permission denied: AH00072: make_sock: could not bind to address 0.0.0.0:80
这个错是因为没用root权限。。


- sudo apt-get install apache2-dev //装apxs
- make是出现问题。。百度google。
- sudo apt-get install python-dev


## Nodejs & Hexo next

### Node
- 官网上下载[Linux Binaries (.tar.xz)]版的(https://nodejs.org/zh-cn/download/)
- `scp -r node-xxx.tar.gz ubuntu@123.206.196.117:~/` 传送到用户目录下，记得压缩文件发过去，解压后发慢的要哭。。
- `tar -xvf node-xxx.tar.gz` 解压 bin目录下就就可以直接node了。
	- `./bin/node =v`
	- `./bin/npm`
- 下一步要吧node和npm添加到PATH里
	1. 修改PATH
	2. 或者将其链接到path下。
		- `echo $PATH` 可查看path
		- `sudo ln -s /home/ubuntu/node-v4.5.0-linux-x64/bin/node /usr/local/bin/`要绝对路径。。

### 淘宝源
- 运行`npm config set registry https://registry.npm.taobao.org`

### hexo & next
- `npm install -g hexo-cli`可执行文件hexo在bin目录下。软链接～
- `hexo init hexo`
- `cd hexo`
- `npm install`
- `git clone https://github.com/iissnan/hexo-theme-next themes/next`
- `vim _config.yml` 修改theme 为next
- `hexo s --debug` 在4000端口启动服务

### 部分配置指南
- 根目录下_config.yml 配置文件 注意yaml的书写 **config-set: xxx** 空格！！否则会报大概这样的错`AMLException: cannot read a block mapping entry; a multi line key may not be an implicit key at line 5, column 1`
- [重要配置项](http://theme-next.iissnan.com/getting-started.html#theme-settings)
	- language: zh-Hans
	- 新增一个字段 avatar: http://xxxx/avtar.png 我是使用qq头像，对应的url。也就是说会随着我qq头像的变化。。获取qq头像url的方法有。。。。我是从多说里发现的。。
	- url,root 字段使用设置好，在后面部署时有用。
	- category_map和tag_map 可以添加一下分类的映射.例如这样。在分类页面就不会显示Web开发字样的url了。而是显示webdev
    ```
    category_map:
            Web开发: webdev
            生物信息: bioinformatics
            语音识别: asr
            数据库: database
            全栈探索: fullstack
    ```
- theme目录下next主题下的_config.yml 配置文件
	- 设置menu,menu_icons是fontawesome的图标。
	- scheme选择不同主题
	- socail socail_icons [社交链接](http://theme-next.iissnan.com/theme-settings.html#author-sites)
- [配置多说](http://theme-next.iissnan.com/getting-started.html#comment-system-duoshuo)，[取消UA信息](http://theme-next.iissnan.com/theme-settings.html#duoshuo-ua)
- [LeanCloud显示文章浏览人数](http://oyjt.github.io/2016/04/09/%E4%B8%BA%E5%8D%9A%E5%AE%A2%E6%96%87%E7%AB%A0%E6%B7%BB%E5%8A%A0%E9%98%85%E8%AF%BB%E9%87%8F%E7%BB%9F%E8%AE%A1%E5%8A%9F%E8%83%BD/)
- [显示全站访问量](http://www.jeyzhang.com/hexo-next-add-post-views.html)

### 使用
- `hexo new title` 新建一篇文章再source/_post 目录下
	- 文章分类和标签
	- 再`---`之间设置类似字段即可
	```
	categories: 全栈探索
    tags: [Linux,杂七杂八]
	```
- `hexo new page xxxx` 在source目录下新建一个目录用于显示分类，tag，about什么的。[详情请看](http://theme-next.iissnan.com/theme-settings.html#categories-page)
- `hexo clean` 清除啥的
- `hexo g` 生成静态 到public文件夹下
- `hexo s --debug` 启动服务，就可以浏览了。

### 部署
- public 下是静态文件，软链接到 www 目录下`ln -s xxx /var/www/html/`
- ln 过去后文件名还是public ， 可能会有问题`mv xx xx`一下。
- 然后就可以用ip访问啦。。
- 想办法做出自动化的orz。强行不用`hexo g` 233


