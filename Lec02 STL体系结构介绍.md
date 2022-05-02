### 六大基础部件

* 容器 Containers
* 分配器 Allocators
* 算法 Algorithms
* 迭代器 Iterators
* 适配器 Adapters
* 仿函数 Functors

<img src="https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220502115721614.png" alt="image-20220502115721614" style="zoom:67%;" />

容器将内存的问题解决掉，用户不需要管内存。分配器是用来管理容器的内存。Algorithms中是模板函数。算法与容器中间的桥梁——迭代器 Iterator，这是一种泛化的指针。

仿函数的作用像一个函数。将不同数据喂给仿函数的转化过程是适配器，对容器、迭代器和仿函数都可以进行适配（Adaptor）

STL编程思想与（泛型编程）OOD的不同：STL将对数据的操作（Algorithms）独立出来，而OOD要求将Algorithms放到class中。

<img src="https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220502120352640.png" alt="image-20220502120352640" style="zoom:67%;" />

头文件：使用任何一种容器都要include它的头文件。<>就是模板，第一个参数是数据类型，第二个是分配器（缺省使用默认分配器）

`count_if`是算法. 绝大多数容器都有`begin`和`end`这两个iterator. `less<>()`是一个仿函数,`bind2nd`是一个adapter--绑定第二个参数(40), `not1`也是一个适配器--非. 

复杂度:容器或分配器等的选用取决于数据的分布(具体情况). 

### 前闭后开的区间

<img src="https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220502121847900.png" alt="image-20220502121847900" style="zoom:50%;" />

标准库规定: `begin()`指向第一个元素的起点, `end()`指向最后一个元素的下一个位置. 遍历整个容器时可以以`end`作为结束的分界. iterator可以做++, --等计算.

 ### range-based for statement (更推荐)

<img src="https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220502122833849.png" alt="image-20220502122833849" style="zoom: 67%;" />

*coll* 表示任何一个容器, 或者是直接给{}. *程序员要清楚变量的类型, 而不是泛滥地使用`auto`*. 只有使用 `&` 取出来的才是元素本身.

