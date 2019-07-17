
# Hive分区

目的

    加快查询
    一般 SELECT 查询会扫描整个表，使用 PARTITIONED BY 子句建表，查询就可以利用分区剪枝（input pruning）的特性


效果
    
    目录下面设置子目录 
    
    分区 相当于 HDFS子目录 
    
# 使用

创建

    按照字段分区
    必须在表定义时指定对应的partition字段

    对多1000各分区

    建表的时候指定partition    
    不用重复定义在 列 信息中
查看

    Hive查询表的分区信息语法：
    SHOW PARTITIONS day_hour_table; 

添加

    ALTER TABLE day_table ADD PARTITION (dt='2008-08-08', hour='08')   
        ALTER partition 
            添加 分区值数量 而不是 规则

删除

    用户可以用 ALTER TABLE DROP PARTITION 来删除分区

    
使用

    SELECT day_table.* FROM day_table WHERE day_table.dt>= '2008-08-08'; 
    
    分区表的意义在于优化查询。查询时尽量利用分区字段。如果不使用分区字段，就会全部扫描。


导入

    预先导入分区数据，但是无法识别怎么办
    Msck repair table tablename
    直接添加分区
    
    分区 和 元数据
    
    分区不是元数据
    先有带分区的数据 后建分区不匹配的表 无法识别  
    
    MSCK 恢复分区 
    


# 单分区 多分区        
    
单分区

    
双分区

       分区顺序不作用
       添加分区 值  删除分区值 
       
    

 # 静态分区
 
 
     静态分区
     load 的时候 添加 分区 并添加数据值
     
     
     LOAD DATA INPATH '/user/pv.txt' INTO TABLE day_hour_table PARTITION(dt='2008-08- 08', hour='08'); 
     LOAD DATA local INPATH '/user/hua/*' INTO TABLE day_hour partition(dt='2010-07- 07');
     
     当数据被加载至表中时，不会对数据进行任何转换。Load操作只是将数据复制至Hive表对应的位置。数据加载时在表下自动创建一个目录
     


# 动态分区
    
    开启支持动态分区
    set hive.exec.dynamic.partition=true;
    默认：true
    set hive.exec.dynamic.partition.mode=nostrict;
    默认：strict（至少有一个分区列是静态分区）
    相关参数
    set hive.exec.max.dynamic.partitions.pernode;
    每一个执行mr节点上，允许创建的动态分区的最大数量(100)
    set hive.exec.max.dynamic.partitions;
    所有执行mr节点上，允许创建的所有动态分区的最大数量(1000)
    set hive.exec.max.created.files;
    所有的mr job允许创建的文件的最大数量(100000)
    

        加载数据
        from psn21
        insert overwrite table psn22 partition(age, sex)  
        select id, name, age, sex, likes, address distribute by age, sex;

