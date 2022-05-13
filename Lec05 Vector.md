 ## Vector

两倍扩充。

没有任何一个东西可以在原地扩充。所以array要扩充的话一定要另找一个地方扩充。

![image-20220513161651433](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220513161651433.png)

如果无法找到两倍大小的空间，那么vector的生命周期就结束了。

vector只需要start、finish和end_of_storage三个指针就可以控制整个容器，因此sizeof(vector)的大小为12(3Byte)

**size()使用两次函数调用来返回size的好处**: 如果begin和end有变化, size也可以不变

![image-20220513174050974](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220513174050974.png)

当`begin==end()`时判断数组`empty`

**两倍增长**:

当`end()==end_of_storage`时就两倍增长. 两倍增长时先计算新的len, 然后调用allocator::allocateO()来分配空间. 接下来拷贝原来的元素到新的空间, 并将新的元素放进去.

但是还会把安插点之后的原内容也拷贝过来, *这是因为`insert_alluxiry()`函数也可能被`insert()`函数调用*

**迭代器**: vector的迭代器不必设计成class, 可以直接使用native pointer. Algorithm库通过Traits获取iterator(native pointer)属性.