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
- Set：set集合是一种不包含重复元素的无序集合, Set集合中主要有两个实现类：HashSet类和TreeSet类 。实现该接口只能使用增强for循环和迭代器来循环，因为实现该接口无下标，添加多个重复只有一个添加成功
	- HashSet:HashSet类是对AbstractSet类的扩张，该类实现了 `Set`接口，通过一个哈希表支持（实际上是一个 `HashMap`实例）， 它没有保证的集合的迭代顺序，hashmap 哈希表边存放的是哈希值，HashSet通过hashcode和equals方法进行判断元素是否重复。注意该实现不同步，如果多个线程访问一个散列集的同时，并至少有一个线程修改的集合，它必须同步外部。HashSet集合采用通过hash算法来决定元素的存储位置不同
	- linkedHashSet: 是一个双向链表，保证插入的元素是有序的
	- TreeSet:实现Set集合的有序集合，TreeSet采用二叉树的数据结构来存储集合元素，TreeSet对加入元素默认按照升序进行排序，
      - TreeSet的排序原理：TreeSet调用元素的compareTo方法来比较元素之间的大小关系，然后将元素按升序或降序排列，因此待加入的元素必须实现compareTo方法，并通过compareTo方法比较两个元素内容的大小
- List：

### 算法
#### 排序算法
- 9大排序算法：5大类 插入、交换、选择、归并、基数

  1. 插入排序：直接插入排序、二分法插入排序、希尔排序。

  2. 选择排序：直接选择排序、堆排序。

  3. 交换排序：冒泡排序、快速排序。

  4. 归并排序。

  5. 基数排序。

     | 排序方法     | 时间复杂度（平均） | 时间复杂度（最坏) | 时间复杂度（最好) | 空间复杂度 | 稳定性 | 复杂性 |
     | ------------ | ------------------ | ----------------- | ----------------- | ---------- | ------ | ------ |
     | 直接插入排序 | O(n2)              | O(n2)             | O(n)              | O(1)       | 稳定   | 简单   |
     | 希尔排序     | O(nlog2n)          | O(n2)             | O(n)              | O(1)       | 不稳定 | 较复杂 |
     | 直接选择排序 | O(n2)              | O(n2)             | O(n2)             | O(1)       | 不稳定 | 简单   |
     | 堆排序       | O(nlog2n)          | O(nlog2n)         | O(nlog2n)         | O(1)       | 不稳定 | 较复杂 |
     | 冒泡排序     | O(n2)              | O(n2)             | O(n)O(n)          | O(1)       | 稳定   | 简单   |
     | 快速排序     | O(nlog2n)          | O(n2)             | O(nlog2n)         | O(nlog2n)  | 不稳定 | 较复杂 |
     | 归并排序     | O(nlog2n)          | O(nlog2n)         | O(nlog2n)         | O(n)       | 稳定   | 较复杂 |
     | 基数排序     | O(d(n+r))          | O(d(n+r))         | O(d(n+r))         | O(n+r)     | 稳定   | 较复杂 |

     - 插入排序：直接插入排序、二分法插入排序、希尔排序
       - 直接插入排序： 每步将一个待排序的记录，按其顺序码大小插入到前面已经排序的字序列的合适位置，直到全部插入排序完为止。 在前面已经排好序的序列中找到合适的插入位置。
       - 
       ```java
       Integer[] testArr = {11,4,8,2,3,0,9,7,5};
       // 插入排序
       for(int i=1;i<testArr.length;i++){
           for (int j=i;j>0 && testArr[j] < testArr[j-1];j--){
               testArr[j] += testArr[j-1];
               testArr[j-1] = testArr[j] - testArr[j-1];
               testArr[j] -= testArr[j-1];
       
           }
           final StringBuffer sb = new StringBuffer();
           Stream.of(testArr).forEach((integer -> sb.append(integer+",")));
           System.out.println(sb.deleteCharAt(sb.length()-1).toString());
       }
       ```
       - 二分插入排序：按二分法找到合适位置插入
       - 
       ```
       
       ```



# 临时记录

- @See 注解
- ReentrantLock 重入锁：
  - 公平锁：线程获取锁的顺序是按照锁的顺序来的
  - 非公平锁：抢锁机制，先lock的线程不一定先获得锁
- transient关键字：<font color="00999ff">当对象被序列化时（写入字节序列到目标文件）时，transient阻止实例中那些用此关键字声明的变量持久化；当对象被反序列化时（从源文件读取字节序列进行重构），这样的实例变量值不会被持久化和恢复</font>