
# 数据类型

    Hive支持关系型数据库中的大多数基本数据类型,
    也支持3种集合数据类型.

# 基本数据类型
  
    string
    int
    
      
# 集合数据类型

    struct map array
    
struct 

map 

array

# 分隔符

概述

    使用分隔符明确数据格式
    
分隔符

    默认分隔符 
        列分隔符   显示^A 实际 ctrl c  也相当与  \u0001 
        集合分隔符 显示^B 实际 ctrl c  也相当与  \u0002 
        映射分隔符 显示^C 实际 ctrl c  也相当与  \u0003 
    自定义分隔符 

示例
     
    create external table psn7(
        id int,
        name string,
        likes array<string>,
        address map<string,string>
    )
    row format delimited
    fields terminated by ','
    collection items terminated by '-'
    map keys terminated by ':';






              