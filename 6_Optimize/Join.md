

# Join

    
    Hive 只支持等值连接（equality joins）、外连接（outer joins）和（left semi joins）。Hive 不支持所有非等值的连接，因为非等值连接非常难转化到 map/reduce 任务
    LEFT，RIGHT和FULL OUTER关键字用于处理join中空记录的情况
    LEFT SEMI JOIN 是 IN/EXISTS 子查询的一种更高效的实现
    join 时，每次 map/reduce 任务的逻辑是这样的：reducer 会缓存 join 序列中除了最后一个表的所有表的记录，再通过最后一个表将结果序列化到文件系统
    实践中，应该把最大的那个表写在最后
    join 查询时，需要注意几个关键点
    只支持等值join
    SELECT a.* FROM a JOIN b ON (a.id = b.id)


    LEFT SEMI JOIN
    LEFT SEMI JOIN 的限制是， JOIN 子句中右边的表只能在 ON 子句中设置过滤条件，在 WHERE 子句、SELECT 子句或其他地方过滤都不行
    SELECT a.key, a.value 
    FROM a 
    WHERE a.key in 
    (SELECT b.key 
    FROM B);
    可以被重写为：
    SELECT a.key, a.val 
    FROM a LEFT SEMI JOIN b on (a.key = b.key)


优化

    semi join 替代 in any
    驱动表为小表  
    
    map join   
        mapreduce join 原理
        提前到map 减少过程
        将小表 加到内存 
    
        开启自动


大表join大表

    单个reduce压力大
    
    空key过滤
    空key转换
        reduce 均匀
    
    
    Join计算时，将小表（驱动表）放在join的左边
    Map Join：在Map端完成Join
    两种实现方式：
    1、SQL方式，在SQL语句中添加MapJoin标记（mapjoin hint）
    语法：
    SELECT  /*+ MAPJOIN(smallTable) */  smallTable.key,  bigTable.value 
    FROM  smallTable  JOIN  bigTable  ON  smallTable.key  =  bigTable.key;
    2、开启自动的MapJoin
    自动的mapjoin
    通过修改以下配置启用自动的mapjoin：
    set hive.auto.convert.join = true;
    （该参数为true时，Hive自动对左边的表统计量，如果是小表就加入内存，即对小表使用Map join）
    
    相关配置参数：
    hive.mapjoin.smalltable.filesize;  
    （大表小表判断的阈值，如果表的大小小于该值则会被加载到内存中运行）
    hive.ignore.mapjoin.hint；
    （默认值：true；是否忽略mapjoin hint 即mapjoin标记）
    hive.auto.convert.join.noconditionaltask;
    （默认值：true；将普通的join转化为普通的mapjoin时，是否将多个mapjoin转化为一个mapjoin）
    hive.auto.convert.join.noconditionaltask.size;
    （将多个mapjoin转化为一个mapjoin时，其表的最大值）
    
    
    
  