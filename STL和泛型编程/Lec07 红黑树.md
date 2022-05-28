# 红黑树

关联式的容器在STL中是由两个数据结构来做的：**红黑树**和**散列表**

 红黑树是高度平衡的二叉搜索树，排列规则有利于search和insert。红黑树提供“遍历”操作及iterator，按照正常规则遍历就可以得到*排序状态（sorted）*但是**不应该使用iterator改变元素值**

红黑树提供两种insert操作：`insert_unique()`，`insert_equal()`。前者表示key独一无二，后者表示key可重复

 2.9版本中红黑树大小为12B

![image-20220517102632050](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220517102632050.png)

Compare是一个仿函数（也称函数对象，行为像函数，理论大小为0），但是定义出对象以后的大小为1，所以总的使用的内存为4+4+1=9，内存对齐后变为12.

`insert_unique()`如果插入重复的元素，不会出错，但是实际上重复的元素只被插了一次。