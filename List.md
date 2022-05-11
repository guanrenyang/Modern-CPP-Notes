# List

list是一个环状双向链表. 里面只有一个元素--一个指针. 这个指针是一个结点的指针, 节点内有三个元素: 1. prev指针 2. next指针 3. data元素值.  

GCC 2.9版中,  prev和next指针都是void*, 后面必须要再进行转型.

所有的container都必须typedef一个类型, 名叫`iterator`, 所有的iterator一定要进行五个typedef, 并且要进行操作符重载. 

iterator当中有一个指针node, 指向某个结点. prefix  ++就是将node.next赋值给node.  

![image-20220511115031043](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220511115031043.png)**看源码要细细分析**: `self tmp = *this`不会唤起重载的*, 因为唤起重载的=是, \*this已经被解析为=的参数.

![image-20220511115410591](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220511115410591.png)

postfix ++返回值, prefix ++返回&,

![image-20220511174341925](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220511174341925.png)

List是一个**带虚头节点**的双向链表, begin()返回虚头结点的下一个元素, end()返回虚头结点