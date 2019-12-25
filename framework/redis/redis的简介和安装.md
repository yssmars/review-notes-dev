## redis简介
redis是全完开源免费的，遵守BSD协议，是一种高性能的key-value的nosql数据库。
Redis是一个开源的使用ANSIC语言编写、支持网络、可基于内存亦可持久化的日志型、Key-Value数据库，并提供多种语言的API。从2010年3月15日起，Redis的开发工作由VMware主持。从2013年5月开始，Redis的开发由Pivotal赞助。

- ### 什么是BSD协议

    - BSD开源协议是一个给于使用者很大自由的协议。
    - 可以自由的使用，修改源代码，也可以将修改后的代码作为开源或者专有软件再发布。
    - BSD代码鼓励代码共享，但需要尊重代码作者的著作权。
    - BSD由于允许使用者修改和重新发布代码，也允许使用或在BSD代码上开发商业软件发布和销售，因此是对商业集成很友好的协议

- ### 什么是nosql
    - NoSQL，泛指非关系型的数据库。
    - 随着互联网web2.0网站的兴起，传统的关系数据库在应付web2.0网站，特别是超大规模和高并发的SNS类型的web2.0纯动态网站已经显得力不从心，暴露了很多难以克服的问题，而非关系型的数据库则由于其本身的特点得到了非常迅速的发展。
    - NoSQL数据库的产生就是为了解决大规模数据集合多重数据种类带来的挑战，尤其是大数据应用难题。
- ### NoSQL数据库的四大分类
    - **键值(Key-Value)存储数据库:**
        这一类数据库主要会使用到一个哈希表，这个表中有一个特定的键和一个指针指向特定的数据。Key/value模型对于IT系统来说的优势在于简单、易部署。但是如果DBA只对部分值进行查询或更新的时候，Key/value就显得效率低下了。举例如：Tokyo Cabinet/Tyrant, Redis, Voldemort, Oracle BDB.
    - **列存储数据库:**
        这部分数据库通常是用来应对分布式存储的海量数据。键仍然存在，但是它们的特点是指向了多个列。这些列是由列家族来安排的。如：Cassandra, HBase, Riak.
    - **文档型数据库:**
        文档型数据库的灵感是来自于Lotus Notes办公软件的，而且它同第一种键值存储相类似。该类型的数据模型是版本化的文档，半结构化的文档以特定的格式存储，比如JSON。文档型数据库可 以看作是键值数据库的升级版，允许之间嵌套键值。而且文档型数据库比键值数据库的查询效率更高。如：CouchDB, MongoDb. 国内也有文档型数据库SequoiaDB，已经开源。
    - **图形(Graph)数据库:**
        图形结构的数据库同其他行列以及刚性结构的SQL数据库不同，它是使用灵活的图形模型，并且能够扩展到多个服务器上。NoSQL数据库没有标准的查询语言(SQL)，因此进行数据库查询需要制定数据模型。许多NoSQL数据库都有REST式的数据接口或者查询API.如：Neo4J, InfoGrid, Infinite Graph.

## redis的特点

- 性能极高：读的速度是110000次/s,写的速度是81000次/s
- 数据类型丰富：string，hash，list，set及zset(sorted set)。
- 原子性：命令的原子性，意思是：一个操作的不可以再分，操作要么执行，要么不执行。
- 数据持久化：持久化功能有效地避免因进程退出造成的数据丢失问题，下次重启时利用之前持久化的文件即可实现数据恢复。

## redis安装

### windows下安装（不推荐）
1. 下载地址：https://github.com/MSOpenTech/redis/releases
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Win_下载.png)
2. 解压到文件夹
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Win_解压.png)
3. 打开一个 cmd 窗口 使用 cd 命令切换目录到 F:\redis 运行redis-server.exe
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Win_启动服务.png)
4. 另启一个 cmd 窗口，原来的不要关闭，不然就无法访问服务端，切换到 redis 目录下运行redis-cli.exe
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Win_客户端.png)

### Linux下安装
1. 下载redis ：wget http://download.redis.io/releases/redis-5.0.5.tar.gz
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Linux_下载.png)
2. 解压：tar xzf redis-5.0.5.tar.gz
3. 进入文件夹：cd redis-5.0.5
4. 编译 make
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Linux_编译.png)
5. 进入src目录 cd src
6. 执行 ./redis-server
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Linux_启动服务.png)
7. 新开一个界面 同样进入到src目录
8. 执行 ./redis-cli
    ![stream_watermark_in_order](https://blog-review-notes.oss-cn-beijing.aliyuncs.com/framework/redis/_images/Linux_客户端.png)