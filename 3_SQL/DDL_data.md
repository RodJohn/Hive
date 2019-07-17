# 复杂格式

    对于复杂格式的原始数据处理


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

# 正则

    Hive正则匹配
     CREATE TABLE logtbl (
        host STRING,
        identity STRING,
        t_user STRING,
        time STRING,
        request STRING,
        referer STRING,
        agent STRING)
      ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.RegexSerDe'
      WITH SERDEPROPERTIES (
        "input.regex" = "([^ ]*) ([^ ]*) ([^ ]*) \\[(.*)\\] \"(.*)\" (-|[0-9]*) (-|[0-9]*)"
      )
      STORED AS TEXTFILE;
      
 