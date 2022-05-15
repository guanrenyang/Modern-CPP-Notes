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