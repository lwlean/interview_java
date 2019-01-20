# 面试
## 数据结构
####  队列
- Queue：先进先出的数据结构 ，接口，和Set,List 都实现了Collection接口，队列不允许随机访问队列中的元素
- Queue：方法
  - add(E)	增加一个元素  队列满会抛出异常
  - offer(E) 		添加一个元素并返回 True 队列满则返回False
  - remove()		删除第一个元素并返回删除的元素 队列为空抛出异常
  - poll() 	删除并返回头部元素，如果队列为空则返回Null
  - element()  返回队列头部的元素 队列为空则抛出异常
  - peek()	返回队列头部的元素 如果队列为空则返回Null
- Queue：接口和实现类
  - BlockingQueue:阻塞队列 不允许插入null值，增加入队方法put(),出队方法take(),以及超时offer和poll，常用语生产者和消费者模式，阻塞用到了ReentrantLock
    - ArrayBlockingQueue:数组结构构成的有界阻塞队列，需要指定大小（和公平和非公平锁，初始化的时候加入默认集合）  [阻塞队列解析](https://blog.csdn.net/javazejian/article/details/77410889 "LinkedBlockingQueue ArrayBlockingQueue")
    - LinkedBlockingQueue:链表结构组成的有界阻塞队列（大小为Integer.Max_Value）建议手动添加大小防止造成机器负担，与ArrayBlockingQueue的区别是使用takeLock和putLock两个对并发控制，添加和删除不是互斥的，吞吐量比ArrayBlockingQueue要大
    - PriorityBlockingQueue:支持优先级排序的无界有序阻塞队列，不支持插入null元素，不支持插入非comparable
    - SynchronousQueue:不储存元素的阻塞队列
    - LinkedTransferQueue:链表结构的无界阻塞队列
    - LinkedBlockingDeque:链表结构的双线阻塞队列
  - PriorityQueue：
  - Deque:双端队列

####  集合
- Set：
- List：



# 临时记录

- @See 注解
- ReentrantLock 重入锁：
  - 公平锁：线程获取锁的顺序是按照锁的顺序来的
  - 非公平锁：抢锁机制，先lock的线程不一定先获得锁
- transient关键字：<font color="00999ff">当对象被序列化时（写入字节序列到目标文件）时，transient阻止实例中那些用此关键字声明的变量持久化；当对象被反序列化时（从源文件读取字节序列进行重构），这样的实例变量值不会被持久化和恢复</font>