

本质是MapReduce
核心思想：把Hive SQL 当做Mapreduce程序去优化
以下SQL不会转为Mapreduce来执行
select仅查询本表字段
where仅对本表字段做条件过滤



# 抓取策略

    理论上SQL会转换为MR
    但是通过抓取策略的设置 

Hive抓取策略：
Hive中对某些情况的查询不需要使用MapReduce计算

抓取策略 
Set hive.fetch.task.conversion=none/more;


一般不改
    
# 执行计划

explain[extends]

anti包 


# 运行方式
    
    本地 快
    集群 默认
    
    开启本地模式：
    set hive.exec.mode.local.auto=true;
    注意：
    hive.exec.mode.local.auto.inputbytes.max默认值为128M
    表示加载文件的最大值，若大于该配置仍会以集群方式来运行
    
    
    本地快  测试 开发  ，
        8088 看不到 ，读取的文件不能大于128M  200w条数据
        
# 并行计算

    子任务没有依赖关系
    最多8个
                    
    并行计算
    通过设置以下参数开启并行模式：
    set hive.exec.parallel=true;
    
    注意：hive.exec.parallel.thread.number
    （一次SQL计算中允许并行执行的job个数的最大值）


# 严格模式
提高查询效率

要求

    对于分区表必须使用分区
    orderby 必须 limit
    
    
# orderby


# JOIN


# Map端聚合

    聚合比例
    
    倾斜优化
        相当于comba
   
# 小文件

    小文件和数据倾斜 是大问题    
    
    小文件
    
        不够128也是一个block
    
    合并参数
    
    
    去重统计
    
 合并小文件
 文件数目小，容易在文件存储端造成压力，给hdfs造成压力，影响效率
 
 设置合并属性
 
 是否合并map输出文件：hive.merge.mapfiles=true
 是否合并reduce输出文件：hive.merge.mapredfiles=true;
 合并文件的大小：hive.merge.size.per.task=256*1000*1000
 
    
# 
map

    
   
reduce
 
    默认1 分桶时为通俗
    
    
    