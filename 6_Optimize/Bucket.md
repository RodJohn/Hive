

# 原理
    
    分桶表是对列值取哈希值的方式，将不同数据放到不同文件中存储。
    对于hive中每一个表、分区都可以进一步进行分桶。

# 作用
 

    数据抽样
        数据随机性
    
 
# 开启分桶

    开启支持分桶
    set hive.enforce.bucketing=true;
    默认：false；设置为true之后，mr运行时会根据bucket的个数自动分配reduce task个数。（用户也可以通过mapred.reduce.tasks自己设置reduce任务个数，但分桶时不推荐使用）
    注意：一次作业产生的桶（文件数量）和reduce task个数一致。
    
    clusted into bucket
     
     

桶

    桶个数mapreduce的个数

    求余


# 抽样

    桶表 抽样查询
    select * from bucket_table tablesample(bucket 1 out of 4 on columns);
    
    TABLESAMPLE语法：
    TABLESAMPLE(BUCKET x OUT OF y)
    x：表示从哪个bucket开始抽取数据
    y：必须为该表总bucket数的倍数或因子
    
    
    当表总bucket数为32时
    TABLESAMPLE(BUCKET 3 OUT OF 8)，抽取哪些数据？
    共抽取2（32/16）个bucket的数据，抽取第2、第18（16+2）个bucket的数据
    TABLESAMPLE(BUCKET 3 OUT OF 256)，抽取哪些数据？
    ？


# 示例

    CREATE TABLE psn31( id INT, name STRING, age INT)
    ROW FORMAT DELIMITED FIELDS TERMINATED BY ',';
    
    测试数据：
    1,tom,11
    2,cat,22
    3,dog,33
    4,hive,44
    5,hbase,55
    6,mr,66
    7,alice,77
    8,scala,88
    
            
    

