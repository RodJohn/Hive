
# 概述
     
     虚拟表 
     
     只能查询
     
     相当于一个过程只有在查看时才会执行
     
     show tables 
     
     迭代视图 

# 语法
     
     View语法
     创建视图：
     CREATE VIEW [IF NOT EXISTS] [db_name.]view_name 
       [(column_name [COMMENT column_comment], ...) ]
       [COMMENT view_comment]
       [TBLPROPERTIES (property_name = property_value, ...)]
       AS SELECT ... ;
     查询视图：
     select colums from view;
     删除视图：
     DROP VIEW [IF EXISTS] [db_name.]view_name;
     
     
