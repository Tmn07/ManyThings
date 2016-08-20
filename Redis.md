# Redis

## 简介
- 又是一篇尝鲜的，不求甚解的记录...
- C写的，key-value数据库，基于内存亦可持久化（可以将内存的数据保持再磁盘），主从模式？？
- 读写性能快，支持各种语言
- 最重要的主从还没研究2333

## 安装启动运行
- Ubuntu
	- 	sudo apt-get install redis-server
	- 	redis-server
	- 	redis-cli(redis-cli -h host -p port -a password)会自动开启服务？
	- 	redis-cli shutdown关闭服务

## 使用

### 基本命令
- AUTH 验证密码、CONFIG set requirepass 'pwd'设置密码(重启无效)在配置文件里改
- ECHO 'xxx'
- PING 查看服务是否运行
- QUIT 关闭当前连接
- SELECT 1 切换1数据库。默认为0.
- keys * 
- DBSIZE 当前key数量

### 配置
- Redis 的配置文件位于 Redis 安装目录下，文件名为 redis.conf
	- 文件长这样每一行`CONFIG_SETTING_NAME NEW_CONFIG_VALUE`
- [菜鸟教程的介绍](http://www.runoob.com/redis/redis-conf.html)还没找到官方文档配置项的说明orz
- `CONFIG GET *(XXXX)`
- `CONFIG SET XX XXX`

### keys命令
- `COMMAND KEY_NAME`[部分操作](http://www.runoob.com/redis/redis-keys.html)
- SET,GET,DEL,EXISTS,DUMP(返回序列化?的值),EXPIRE(设置过期时间)，EXPIREAT(接受时间戳),KEYS [pattern],MOVE,RANDOMKEY,RENAME,TYPE

### String

- 	SET url "tmn07.com"//SETNX 只有当key不存在时。。
- 	GET url
- 	GETRANGE url 0 -1
- 	GETSET(返回原值并赋新值)
- 	SETBIT,GETBIT(偏移量?)
- 	SETEX key second value
- 	STRLEN key
- 	MSET[NX] key1 "Hello" key2 "World"
- 	数值型增减.....
- 	APPEND key value 追加

### Hash

- 一个 key 有多个 field(字段) 对应 value。 2^32 - 1 键值对。添加，删除，查找的复杂度都是O(1)
- HDEL key fields(删除一个或多个field)
- HEXISTS key field
- HGET key field
- HGETALL key
- HKEYS key (获取全部fileds)
- HVALS key (获取全部values)
- HLEN key
- HMGET key f1 f2 
- HMSET key f1 v1 f2 v2 (同时将多个 field-value (域-值)对设置到哈希表 key 中。)

### List
- 按插入顺序排序的，列表的头部（L左边）或者尾部（R右边）

### Set——S
- Redis的Set是string类型的无序集合。集合成员是唯一的，这就意味着集合中**不能出现重复**的数据。
- Redis 中 集合是通过哈希表实现的，所以添加，删除，查找的复杂度都是O(1)。

### 有序集合(sorted set)——Z
- hash实现的，value不重复，score可重复，根据score排序，"优先队列"

### Hyper基数？？

### pub/sub消息通信
- 好像很有趣otz[某博客](http://blog.sina.com.cn/s/blog_62b832910100xok2.html)
- subscribe xxx
- psubscibe pattern （订阅符合规则的）
- publish xxx value

### Some
- redis-benchmark 用于性能测试
- 客户端命令CLIENT list , setname,getname,pause,kill
- Redis 管道技术可以在服务端未响应时，客户端可以继续向服务端发送请求，并最终一次性读取所有服务端的响应。
- [关于Redis的一些常识](http://blog.csdn.net/mengxianhua/article/details/8961713)
- [baidu经验。应用场景。](http://jingyan.baidu.com/article/fdbd4277187fb7b89e3f48f2.html)