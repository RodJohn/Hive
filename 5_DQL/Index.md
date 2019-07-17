
# 特点

原理

    生成新的表来存储
    列值 文件 偏移量
    
特点
    
    使用索引查询时,先查索引表，再查数据，不是索引组织表    
    索引必须手动维护
    但是Hive支持索引的建立，但是不能提高Hive的查询速度。
        
        
        
# 创建

语法
    
    create index t1_index on table psn2(name) 
    as 'org.apache.hadoop.hive.ql.index.compact.CompactIndexHandler' with deferred rebuild 
    in table t1_index_table;

解析

    as：指定索引器；
    in table：指定索引表，若不指定默认生成在default__psn2_t1_index__表中
    
# 维护    
        

    重建索引 重建才有数据
    每一次新增数据 都得 重建


# 删除

    drop on    
 