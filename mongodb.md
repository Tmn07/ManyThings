## NoSQL初学习
### 启动服务
- 配置各种文件目录
- mongod.conf
	> port = 12345
	> dbpath = data
	> logpath = log/mongod.log
	> fork = true

- ./bin/mongod -f conf/mongod.conf 开启服务
### 客户端连接
1. 用mongo连接
  -  bin/mongo [options] [db address] [file names (ending in .js)]
  > bin/mongo 127.0.0.1:12345/test
  - ...

2. PHP连接

### 基本操作
- show dbs 库
- show collections 表
- use xxx库  // 会自动生成库
- db.dropDatabase() // 删除当前库
- db.xxx表.insert({json:1})  // 会自动生成表,支持for循环。。
	> for(i=4;i<100;i++)db.zwd.insert({x:i})
- db.xxx表.find() //默认返回所有
	>  db.zwd.find().skip(3).limit(2).sort({x:1}) // skip跳过前几条，limit限制输出，sort排序？？
