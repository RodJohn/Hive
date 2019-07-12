



# 数据类型

Hive支持关系型数据库中的大多数基本数据类型,
同时也支持关系型数据库中很少出现的3种集合数据类型.
  
  1 基本数据类型、
  
  
集合数据类型
Hive中列支持使用struct map array集合数据类型.



# DDL

建库


建表

     CREATE TABLE person(
        id INT,
        name STRING,
        age INT,
        likes ARRAY<STRING>,
        address MAP<STRING,STRING>
      )
      

查看

    select * from TBLS  （mysql）

    desc formatted    
        
        input
        output
        stroage desc param 分割  
      

      table type 
      
Hive 建表

Create Table Like:
CREATE TABLE empty_key_value_store LIKE key_value_store;

Create Table As Select (CTAS)
CREATE TABLE new_key_value_store 
      AS
    SELECT columA, columB FROM key_value_store;




# 表类型

desc formatted    

      table type 
        managetype 
        tempart     临时表
        外部表
        
外部表 

    建表关键字 
    
    location
        默认 hive-site
        指定
        
内部表和外部表的区别
    建表 内部表使用默认路径 外部表需要指定路径
    删除 外部表只删除元数据，不删除数据 内部表全部删除         
    优点     
       内部表 先建表 后加载数据
       外部表 HDFS先有数据 在建表
       
Hive 内部表
CREATE  TABLE [IF NOT EXISTS] table_name
删除表时，元数据与数据都会被删除
Hive 外部表
CREATE EXTERNAL TABLE [IF NOT EXISTS] table_name LOCATION hdfs_path
删除外部表只删除metastore的元数据，不删除hdfs中的表数据




    
              