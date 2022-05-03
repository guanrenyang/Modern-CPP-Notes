Lec 03

需要知道内存中的样子才能知道效率。

容器的分类：1. 序列式 2. 关联式——元素是有key和value，可以用key来找value，适合做快速的查找。

Unordered Containers: C++11新出现的容器, 它也是一种关联性容器, 它本质上是hash table做的. 

Array和Forward-List也是C++11新出现的.

Sequence Container: 

![image-20220503102302205](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220503102302205.png)

Array: 固定长度的数组

Vector: 起点不能动, 尾部是无限扩充的, 内存会自动增长, 由分配器来管理. 

Deque: 两头可进可出

List: 双向(环状)链表, 环状只是为了功能上的便利性.

Forward-List: 单向链表. *使用List所用的内存一定比List多, 因为至少多存一个指针. *

Associative Containers:

![image-20220503103842323](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220503103842323.png)

Set和Map: 实际上是使用红黑树做的(标准库没有规定用什么做, 但是各家编译器都用红黑树做)

Map可以用Key来找Value, Set的Key就是Value. Multiset和Multiset表示元素可以重复(Set和Map的Key不能重复)



Unordered Containers

![image-20220503103549324](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220503103549324.png)

公认最好的hash做法是Separate Chaining的做法.

```c++
array<long, 10> c;
c.data()// array.data()返回数组再内存里面起点的地址 
```

*array* 必须指明长度. 

Vector的`push_front`需要把整个数组向后推一格。  