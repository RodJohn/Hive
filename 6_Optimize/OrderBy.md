
   
    
    
#  Order 

    ORDER BY与SORT BY的不同
    ORDER BY 全局排序，只有一个Reduce任务
    SORT BY 只在本机做排序

原理

    全排序
    一个
    
改进
    
    sort by + distruct by
    
    clusterby 
    
    Order By - 对于查询结果做全排序，只允许有一个reduce处理
    （当数据量较大时，应慎用。严格模式下，必须结合limit来使用）
    Sort By - 对于单个reduce的数据进行排序
    Distribute By - 分区排序，经常和Sort By结合使用
    Cluster By - 相当于 Sort By + Distribute By
    （Cluster By不能通过asc、desc的方式指定排序规则；
    可通过 distribute by column sort by column asc|desc 的方式）    
        
