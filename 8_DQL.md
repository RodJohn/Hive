

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

#  Order 

    ORDER BY与SORT BY的不同
    ORDER BY 全局排序，只有一个Reduce任务
    SORT BY 只在本机做排序


# REGEX Column Specification

    SELECT 语句可以使用正则表达式做列选择，下面的语句查询除了 ds 和 hr 之外的所有列：
    SELECT `(ds|hr)?+.+` FROM test
    
    抓取复杂类型
    
    使用正则  匹配 抓取 
    
