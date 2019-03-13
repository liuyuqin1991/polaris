## redis常用命令
1. INCR KEY  指定key+1
2. KEYS pattern 
- 使用范例：keys k1*  找到所有开头为k1的key
- 数据量巨大时会有性能问题
3. SCAN cursor [MATCH pattern] [COUNT count]
- 使用范例：scan 0 match k1* count 10 从游标0开始返回10个匹配的数据和下一个游标
- 数量不固定且可能有重复，需要程序处理
4. expire key seconds 设置过期时间（秒）
5. setnx key value 如果key不存在则创建并赋值，成功返回1 key存在返回0 （用于同一时间执行一次的操作）
6. set key value [EX seconds] [PX milliseconds] [NX|XX]
- ex 设置过期时间单位为秒 px设置过期时间为毫秒
- nx 只有键不存在时才会操作 xx 只有键存在时才会进行操作
- 使用范例：set keename 111 ex 10 nx
## redis数据结构相关问题
1. hash结构使用方法：hmset key map  生成一个key和map对象 | hget key mapkey 得到key对应的mapkey的值 | hset key mapkey mapvalue 给map赋值
2. list使用方法：lpush key value 从keylist头上插入一个值 | lrange key 0 10 输出keylist前10个 
 - list实现异步队列的方法：rpush 从末尾加入元素 | lpop 从头取出元素 | blpop key timeout 阻塞队列直到有消息或者超时 | 
 - 订阅模式队列  subscribe topicName 订阅频道 | pulish topicname value 发送消息到对应频道
3. set使用方法：sadd key value 向keyset加入元素 | smembers key 取出set中的元素
4. shorted set使用方法：zadd key SCORE value 这是一个带有排序的set 排序的标准就是用的score | zrangebyscore key 0 10 取出set的方法
