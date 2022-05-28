# Deque

Deque是一种双向开口的线性表。  

![image-20220515100843279](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220515100843279.png)

deque使用很多个短buffer来组织元素，buffer的顺序使用一个指针的vector（map）来组织。

deque的迭代器有一个元素`node`，这就是这个deque的“控制中心”，`first`和`last`用于在表示buffer的边界。当iterator加加或减减的时候需要检测边界，如果已经到边界就要跳到下一个buffer。 

所有的容器都维护两个迭代器`start`和`finish`，他们分别是`begin()`和`end()`的返回值。

2.9版本允许指定缓冲区的大小，如果不指定就根据元素大小来调整缓冲区的大小。

**insert**：deque在insert的时候会检测安插的元素距离头和尾的距离。因为insert的时候要移动前或后的所有元素，推短的那一段比较快：

1. 如果安插的元素在最前端（不需要移动），可以交给`push_front()`
2. 如果安插在最尾端，可以交给`push_back()`
3. 如果都不满足， 则判断它靠近头还是尾，

**迭代器之间的距离：** = buffer size \* 中间夹的缓冲区的个数+头尾两个缓冲区当中夹的元素个数

deque需要提供`+=`和`+`两个运算符，如果目标点在同一个缓冲区直接可以加；如果检查完以后发现落在另一个缓冲区，就计算落在那一个缓冲区，找到那一个缓冲区，再决定要走几格。

![image-20220516105317670](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220516105317670.png)

新版本的deque不允许指定buffer size

## Stack

queue和stack的底层使用了一个deque，并封住了deque的一些功能。他们本质上不是container而是adaptor。

stack和queue都不允许遍历，也不提供iterator。

stack和queue都可以选择list或deque作为底层结构。默认的deque比较快。

queue可以不可以选择vector，而stack可以选择vector作为底层结构。如果将vector作为queue的底层容器，那么pop时会出错，因为vector没有`pop_front()`函数

*在使用模板的时候，编译器时不会做全面的检测的。不能用有时只是“局部错误“而已。对于模板编译器不会进行全局的检测。如果代码中确实没用到`pop`那么传vector进去作为底层容器也不会错*

stack和queue都不可以选择set或map作为底层结构（传进去页调用不到底层的正确的函数）。

