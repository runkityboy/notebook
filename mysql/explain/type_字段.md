### 定义
找到数据所是用的扫描类型

### 扫描方式

-   system: 系统表，少量数据，往往不用磁盘IO
    -  查询系统表
    -  select * from (select * from user where id=1) tmp，外层嵌套从内层临时表查询

-   const: 常量连接
    - 命中主键或者唯一索引
    - 被连接的部分是常量

-   eq_ref: `主键索引`或`非空唯一索引`等值扫描
    -  join查询
    -  命中主键或者唯一索引，
    -  等值连接

-   ref: 非`主键索引`和`非空唯一索引`等值扫描
    -  可出现在join或单表普通索引查询
    -  对于前表的每一行，在后表中可出现多条记录满足连接条件
    -  等值连接

-   range: 范围扫描
    - 索引上的范围查询

-   index: 索引树扫描
    - 扫描索引上所有的数据

-   all: 全表扫描



### [参考文档](https://mp.weixin.qq.com/s?__biz=MjM5ODYxMDA5OQ==&mid=2651962514&idx=1&sn=550c48c9395b52b7ec561741e86e5ce0&chksm=bd2d094e8a5a80589117a653a30d062b5760ec20f8ab9e2154a63ab782d3353d1b1da50b9bc2&scene=21#wechat_redirect)

