
     
# REGEX Column Specification

    SELECT 语句可以使用正则表达式做列选择，下面的语句查询除了 ds 和 hr 之外的所有列：
    SELECT `(ds|hr)?+.+` FROM test
    
    抓取复杂类型
    
    使用正则  匹配 抓取 
    
