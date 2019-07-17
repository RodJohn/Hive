

# lateral 

    explote() 缺点 只能一个UDTF
    
    组合 UDTF 函数explote 
    
    hive Lateral View
    Lateral View用于和UDTF函数（explode、split）结合来使用。
    首先通过UDTF函数拆分成多行，再将多行结果组合成一个支持别名的虚拟表。
    主要解决在select使用UDTF做查询过程中，查询只能包含单个UDTF，不能包含其他字段、以及多个UDTF的问题

# 语法

    LATERAL VIEW udtf(expression) tableAlias AS columnAlias (',' columnAlias)



# 示例

    统计人员表中共有多少种爱好、多少个城市?
    
    select count(distinct(myCol1)), count(distinct(myCol2)) from psn2 
    LATERAL VIEW explode(likes) myTable1 AS myCol1 
    LATERAL VIEW explode(address) myTable2 AS myCol2, myCol3;


     