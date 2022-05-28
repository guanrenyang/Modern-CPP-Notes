# 面向对象（OOD）vs 泛型编程（GP）

* OOP：数据和操作放在一个类里

  例如类list有自己的sort函数

* GP：将数据（Data）和方法（Method）分开来。

  例如vector和deque都没有提供sort，而algorithm库中提供了一个sort（可以作用于多种容器）

采用GP的好处：container和algorithms的团队可以独立工作，只要接口（iterator）定好即可。

algorithm通过iterator确定操作的范围，并通过iterator取用container的元素

**list不能使用全局sort的原因**：

![image-20220507210502691](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220507210502691.png)

`first+(last-first)/2`这步操作只有随机访问的迭代器才可以使用。而list使用的迭代器之能从一个跳到下一个。

*所有algorithm内部最终设计的元素本身的操作，无非是**比大小***

