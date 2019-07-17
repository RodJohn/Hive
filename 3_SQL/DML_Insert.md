
   

# 插入

    插入有3种 load 、from insert select、insert
    
## load

    导入数据到Hive

从HDFS导入

    load data inpath ‘/home/wyp/add.txt’ into table wyp;
    
    从HDFS导入数据到表中，相当于移动数据到对应的Hive表的数据目录里面
    
从本地文件系统导入

    load data local inpath 'wyp.txt' into table wyp

    从本地文件系统中将数据导入到Hive表的过程中，
    其实是先将数据临时复制到HDFS的一个目录下（典型的情况是复制到上传用户的HDFS home目录下,比如/home/wyp/），
    然后再将数据从那个临时目录下移动（注意，这里说的是移动，不是复制！）到对应的Hive表的数据目录里面。
    
    
## From insert select 
 
    从指定表查询指定数据插入到其他表中

特点

    一次查询 多次插入  
    中间结果
    可以override
      

## insert 

    慢
    一般不用
    
    insert into table values()

    
# 导出

    导出数据到文件系统
    
    insert into local directory dic.. select-statement
    
    默认分隔符  cat -A 才能看到

   
    
 
    
    
    
     