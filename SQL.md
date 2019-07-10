

都是标准的SQL语句

# DDL

建库


建表

查看表
    
    select * from TBLS  （mysql）

数据类型

    基础类型
    
    特殊类型



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
    
# 示例
数据

建表语句

查看
    desc formatted    
        
        input
        output
        stroage desc param 分割  
      

      table type 
插入数据

    insert 慢
    
    lode 
        本地 文件 或者 hdfs

    create select  like  
    
    
    
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
       
#  读时检查

    读时检查 hive
    写时检查 mysql
    
    读时检查 
        插入时不检查
        解耦
            HDFS 存储 提高存储效率
            Hive 分析  不符合就读取为null
            
    插入数据不匹配
    
                 