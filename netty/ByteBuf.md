### 不使用ByteBuffer的原因
- 操作麻烦，读写公用一个position，容易出问题
- 容量固定，不能动态收缩&扩容

### 实现类的维度
#### 内存分配角度
- 堆内存
  1. 分配和回收速度快
  2. 可被JVM自动回收
  3. 缺点：进行Socket的IO读写，需要额外的一次内存复制

- 直接内存
  1. 分配和回收速度慢
  2. 优点：进行Socket的IO读写，不需要额外的一次内存复制

总结：IO通讯线程的读写缓冲区采用DirectByteBuf, 业务编解码是用HeapByteBuf

#### 内存回收角度
- 基于对象池的ByteBuf  
  循环利用申请的ByteBuf，降低高负载导致的频繁Full GC

- 普通的ByteBuf

### 扩容策略
从64字节开始成倍扩容直到4MB，然后再以4MB步进的方式扩容

###