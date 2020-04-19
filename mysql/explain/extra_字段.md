#### 1. using where
sql使用了where条件过滤数据

#### 2. using index
sql返回的所有列数据均在一颗索引树上，无需回表查

#### 3. using index condition
查询语句命中索引，但是返回结果并不包含所有的列，需要回表查

#### 4. using filesort
得到的结果集需要进行排序, 可以通过在排序列上加索引来优化

#### 5. using temporary
需要中间表来暂存中间结果，典型的场景是sql同时存在`group by`、`order by`,且作用于不同的字段

#### 6. using join buffer (Block Nested Loop)
需要进行嵌套循环计算