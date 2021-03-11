### 解决的问题
同一个对象，不同的线程独立维护不同的副本，比如spring中http请求的request对象

### hash冲突
采用线性探测法

### 内存泄露风险
由于线程池的存在，线程是可以一直存在的，如果ThreadLocal存了一个很大的对象，且忘记回收，那么该大对象会一直存在

### 注意点
1. ThreadLocalMap初始大小为16，负载因子2/3,
   当达到阈值后，尝试清理key=null的元素，如果还是超过阈值，再执行扩容
2. 为什么ThreadLocalMap.Entry要继承WeakReference
   1. 如果ThreadLocal定义为局部变量，且出了局部变量作用范围而忘记调用remove方法，导致对象一直存在无法被收集器回收