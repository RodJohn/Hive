

# 文件

字段 
分隔符
    默认分隔符 
        显示 ^A 实际 ctrl c  也相当与 ^A \u0001 ^B \u0002
    自己定义 
        filed , 
        -
        :
文件格式
    TEXT
    JSON
    
行存储 列存储 
    存储空间  
 


# 1、从本地文件系统中导入数据到Hive表

    load data local inpath 'wyp.txt' into table wyp

存儲

    到wyp表的数据目录下查看
    
    hive> dfs -ls /user/hive/warehouse/wyp ;
    Found 1 items
    -rw-r--r--3 wyp supergroup 67 2014-02-19 18:23 /hive/warehouse/wyp/wyp.txt
    
    从本地文件系统中将数据导入到Hive表的过程中，
    其实是先将数据临时复制到HDFS的一个目录下（典型的情况是复制到上传用户的HDFS home目录下,比如/home/wyp/），
    然后再将数据从那个临时目录下移动（注意，这里说的是移动，不是复制！）到对应的Hive表的数据目录里面。
    
    
# HDFS上导入数据到Hive

load data inpath ‘/home/wyp/add.txt’ into table wyp;里面是没有local这个单词的

    
    
    
    
