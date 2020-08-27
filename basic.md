# 基础知识

## 一、数据结构与算法基础

### 1. 说一下几种常见的排序算法和分别的复杂度

|排序法|最差时间分析|平均时间复杂度|稳定度|空间复杂度|
| :- | :- | :- | :- | :- | :- |
|冒泡排序|O(n2)|O(n2)|稳定|O(1)|
|快速排序|O(n2)|O(n*log2n)|不稳定|O(log2n)~O(n)|
|选择排序|O(n2)|O(n2)|稳定|O(1)|
|二叉树排序|O(n2)|O(n*log2n)|不稳定|O(1)|
|插入排序|O(n2)|O(n2)|稳定|O(1)|
|堆排序|O(n*log2n)|O(n*log2n)|不稳定|O(1)|
|希尔排序|O|O|不稳定|O(1)|

### 2. 用Java写一个冒泡、快速排序算法

#### 冒泡排序

   ``` Java
public static int[] bubbleSort(int a[]) {
    int temp;
    for (int i = 0; i < a.length; i++) {
        for (int j = 0; j < a.length - 1 - i; j++) {
            if (a[j] > a[j + 1]) {
                temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }
    return a;
}
   ```

#### 快速排序

``` Java
public static int[] quickSort(int[] data, int left, int right) {
        int middle, tempData;
        int i = left;
        int j = right;
        middle = data[(i + j) / 2];
        do {
            //找出左边比中间值大的数
            while (data[i] < middle && i < right)
                i++;
            //找出右边比中间值小的数
            while (data[j] > middle && j > left)
                j--;
            //将左边大的数和右边小的数进行替换
            if (i <= j) {
                tempData = data[i];
                data[i] = data[j];
                data[j] = tempData;
                i++;
                j--;
            }
        } while (i <= j);
        if (i < right) {
            quickSort(data, i, right);
        }
        if (j > left) {
            quickSort(data, left, j);
        }
        return data;
    }
```

### 3. 描述一下链式存储结构

### 4. 如何遍历一颗二叉树

- 前序遍历：先访问根节点，再遍历左子树，最后遍历右子树
- 中序遍历：先遍历左子树，然后访问根节点，最后遍历右子树
- 后序遍历：先遍历左子树，然后遍历右子树，最后访问根节点

### 5. 倒排一个LinkedList

>定义一个`LinkedList<Integer> templist = new LinkedList<>()`;  
来存储list里面的值，通过迭代list,将值插入在templist的头上，那么templist  
就是list的反转了，最后将templist赋值给list就行了。

``` Java
public void reverse() {
    LinkedList<Integer> list = new LinkedList<>();
    LinkedList<Integer> templist = new LinkedList<>();
    int i = 0;
    while (i < 6) {
        list.add(i);
        i++;
    }
    Iterator<Integer> it = list.iterator();
    int m;
    while (it.hasNext() && i >= 0) {
        m = it.next();
        templist.addFirst(m);
        i--;
    }
    list = templist;
    System.out.println(list);
  }

```

### 6. 用Java写一个递归遍历目录下面的所有文件

``` Java
public void traverseFolder(String path) {
    File file = new File(path);
    if (!file.exists()) {
        System.out.println("文件不存在!");
        return;
    }
    File[] files = file.listFiles();
    if (files.length == 0) {
        System.out.println("文件夹是空的!");
        return;
    }
    for (File file : files) {
        if (file.isDirectory()) {
            System.out.println("文件夹:" + file.getAbsolutePath());
            traverseFolder(file.getAbsolutePath());
        } else {
            System.out.println("文件:" + file.getAbsolutePath());
        }
    }
}

```

## 二、Java基础

### 1. 接口与抽象类的关系

设计目的：接口是对动作的抽象，抽象类是对根源的抽象。对于抽象类，例如男人、  
女人这两个类，那我们可以为这两个类设计一个更高级别的抽象类 -- 人。对于接口，  
我们可以坐着吃饭、站着吃饭、用筷子吃、用叉子吃等，那么可以把这些吃饭的动作  
抽象成一个接口- -吃饭。所以在高级语言中，一个类只能继承一个抽象类（因为你  
不可能既是生物又是非生物），但是一个类可以实现多个接口，比如开车接口、滑冰  
接口、打球接口等。
> 1）抽象类和接口不能直接实例化。如果抽象类要实例化，那么抽象类定义的变量  
必须指向一个子类，这个子类继承了这个抽象类并且实现了这个抽象类的所有方法。  
如果接口要实例化，那么这个接口定义的变量要指向一个子类对象，这个子类必须实  
现了该接口的所有方法。

### 2. Java中的异常有哪几类，分别怎么使用

### 3. 常用的集合类有哪些，比如List如何排序

### 4. ArrayList和LinkedList内部实现大致是怎样的，它们之间的区别和优缺点

### 5. 内存溢出是怎么回事，举例说明

### 6. ==和equals的区别

### 7. hashCode方法的作用

### 8. NIO是什么，适用于何种场景

### 9. HashMap实现原理，如何保证HashMap的线程安全

### 10. JVM内存结构，为什么需要GC

### 11. NIO模型，select/epoll的区别，多路复用的原理

### 12. Java中一个字符占多少个字节，int、long、double

### 13. 创建一个类的实例都有哪些办法

### 14. final/finally/finalize的区别

### 15. Session/Cookie的区别

### 16. String/StringBuffer/StringBuilder的区别，扩展再问他们的实现

### 17. Servlet的生命周期

### 18. 如何用java分配一段连续的1G的内存空间，需要注意些什么

### 19. Java有自己的内存回收机制，但为什么还存在内存泄漏的问题

### 20. 什么事Java序列化，如何实现Java序列化（写一个实例）

### 21. String s = new String(“abc”);创建了几个String Object

## 三、JVM

### 1. JVM堆得基本结构

### 2. JVM的垃圾算法有哪几种，CMS垃圾回收的基本流程

### 3. JVM有哪些常用启动参数可以调整，描述几个

### 4. 如何查看JVM的内存使用情况

### 5. Java程序是否会内存溢出，内存泄漏情况发生，举几个例子

### 6. 你常用的JVM配置和调优参数都有哪些，分别什么作用

### 7. JVM的内存结构

### 8. 常用的GC策略，什么时候会触发YGC，什么时候触发FGC

## 四、多线程/并发

### 1. 如何创建线程，如何保证线程安全

### 2. 如何实现一个线程安全的数据结构

### 3. 如何避免死锁

### 4. Volatile关键字的作用

### 5. HashMap在多线程环境下使用需要注意什么，为什么

### 6. Java程序中启动一个线程用run()还是start()

### 7. 什么是守护线程，有什么作用

### 8. 什么是死锁，如何避免

### 9. 进程和线程的区别

### 10. Java的Threadlocal是怎么实现的

### 11. ConcurrentHashMap的实现原理

### 12. sleep和wait的区别

### 13. notify和notifyAll区别

### 14. ThreadLocal的作用与实现

### 15. 两个线程如何串行执行

### 16. 上下文切换是什么含义

### 17. 可以运行时kill掉一个线程吗

### 18. 什么是条件锁、读写锁、自旋锁、可重入锁

### 19. 线程池ThreadPoolExecutor的实现原理

## 五、Linux使用与问题分析排查

### 1. 使用两种命令创建一个文件（touch vim）

### 2. 硬链接和软链接的区别

### 3. Linux常用命令有哪些

### 4. 怎么看一个Java线程的资源耗用

### 5. load过高的可能性有哪些

### 6. /etc/host文件什么作用

答： /etc/hosts是配置ip地址和其对应主机名的文件，这里可以记录本机的或其他主机的ip及其对应主机名。

### 7. 如何快速的将一个文本中所有的“abc”替换为“xyz”

 cat file | tr "abc" "xyz" > new_file 这里，凡是在file中出现的"a"字母，都替换成"x"字母，"b"字母替换为"y"字母，"c"字母替换为"z"字母。而不是将字符串"abc"替换为字符串"xyz"。

### 8. 如何log文件中搜索出error的日志

### 9. 发现磁盘空间不够，如何快速找出占用空间最大的文件

### 10. Java服务端问题排查（OOM、CPU高、Load高、类冲突）

### 11. Java常用问题排查工具及用法（top、iostat、vmstat、sar、tcpdump、jvisualvm、jmap、jconsole）

### 12. Thread dump文件如何分析（Runnable、锁、代码栈、操作系统线程id关联）

### 13. 如何查看Java应用的线程信息

## 六、框架使用

### 1. 描述一下Hibernate的三个状态

### 2. Spring中Bean的生命周期

### 3. SpringMVC处理请求的流程

### 4. Spring AOP解决了什么问题，怎么实现的

### 5. Spring事务的传播属性是怎么回事，它会影响什么

### 6. Spring中BeanFactory和FactoryBean有什么区别

### 7. Spring框架中IOC的原理是什么

### 8. Spring的依赖注入有哪几种方式

### 9. 用Spring如何实现一个切面

### 10. Spring如何实现数据库事务

### 11. Hibernate对一二级缓存的使用，Lazy-Load的理解

### 12. Mybatis如何实现批量提交

## 七、数据库相关

### 1. MySQL InnoDB、Mysaim的特点

### 2. 乐观锁和悲观锁的区别

### 3. 数据库隔离级别是什么，有什么作用

### 4. MySQL主备同步的基本原理

### 5. Select * from table t where size>10 group by size order by size 的执行顺序

### 6. 如何优化数据库性能（索引、分库分表、批量操作、分页算法、升级硬盘ssd、业务优化、主从部署）

### 7. SQL什么情况下不会使用索引（不包含、不等于、函数）

### 8. 一般在什么字段上建立索引（过滤数据最多的字段

### 9. 如何从一张表中查出name字段不包含“XYZ”的所有行

### 10. MySQL、B+索引实现、行锁实现、SQL优化

### 11. Redis、RDB和AOF如何做高可用、集群

### 12. 如何解决高并发减库存问题

### 13. mysql存储引擎中索引的实现机制

### 14. 数据库事务的几种粒度

### 15. 行锁、表锁、乐观锁、悲观锁

## 八、网络协议和网络编程

### 1. TCP建立连接的过程

### 2. TCP断开连接的工程

### 3. 浏览器发生302跳转背后的逻辑

### 4. HTTP协议的交互流程，HTTP和HTTPS的差异，SSL的交互流程

### 5. Rest和HTTP有什么关系，大家都说Rest很轻量，你对Rest风格如何理解

### 6. TCP的滑动窗口协议有什么作用，讲讲原理

### 7. HTTP协议都有哪些方法

### 8. 交换机和路由器的区别

### 9. Socket交互的基本流程

### 10. HTTP协议（报文结构、断点续传、多线程下载、什么是长连接）

### 11. Tcp协议（建连过程、慢启动、滑动窗口、七层模型）

### 12. Webservice协议（wsdl/soap格式，与Rest协议的区别）

### 13. NIO的好处、Netty线程模型，什么是零拷贝

## 九、Redis等缓存系统/中间件/NoSQL/一致性Hash等

### 1. 列举一个常用的Redis客户端的并发模型

### 2. Hbase如何实现模糊查询

### 3. 列举一个常用的消息中间件，如果消息要保序如何实现

### 4. 如何实现一个Hashtable，你的设计如何考虑Hash冲突，如何优化

### 5. 分布式缓存，一致性hash

### 6. LRU算法，slab分配，如何减少内存碎片

### 7. 如何解决缓存单机热点问题

### 8. 什么是布隆过滤器，其实现原理是，False positive指的是什么

### 9. memcache与redis的区别

### 10. zookeeper有什么功能，选举算法如何进行

### 11. map/reduce过程，如何用map/reduce实现两个数据源的联合统计

## 十、设计模式与重构

### 1. 你能举例几个常见的设计模式

### 2. 你在设计一个工厂的包的时候会遵循哪些原则

### 3. 你能列举一个使用了Visitor/Decorator模式的开源项目/库

### 4. 你在编码时最常用的设计模式有哪些，在什么场景下用

### 5. 如何实现一个单例

### 6. 代理模式（动态代理）

### 7. 单例模式（懒汉模式、恶汉模式、并发初始化如何解决，volatile与lock的使用）

### 8. JDK源码里面都有些什么让你印象深刻的设计模式使用
