
# 数据库操作

创建数据库

    create database myhive;

查看数据库

    show databases;


# 创建表

## 普通类型

     CREATE TABLE person(
        id INT,
        name STRING
      )

## 复杂类型

概述

    复杂类型需要使用分隔符进行分割
    
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
    address map<string,string>)
    row format delimited
    fields terminated by ','
    collection items terminated by '-'
    map keys terminated by ':';

# 创建外部表

概述

    使用external标识的表就是外部表
    外部表相当于HDFS文件的一个引用

语法

    create external table text1 (line string) location '/user/input/'
    基于HDFS创建表
    文件是'/user/input/word'，使用它的目录

        
## 内部表和外部表区别

建表时

    内部表 先建表 后加载数据
    外部表 HDFS先有数据 在建表
      
删除时

    外部表只删除metastore的元数据，不删除hdfs中的数据
    内部表元数据与数据都会被删除


# 复制表

Like

    CREATE TABLE person1 LIKE person;
    只复制表结构

As

    Create person2 As Select id,name from person
    创建表并导入数据

# 查看表

hive

    desc formatted person   
        
        input
        output
        stroage desc param 分割  
      
mysql

    select * from TBLS  （mysql）
      




    
              