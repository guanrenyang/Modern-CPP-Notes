# explicit

1. explicit关键词用地很少，主要就是用在构造函数身上

2. 左边的5会自动调用构造函数创建Complex对象，但是右边的使用explicit要求显示调用，所以会报错

   ![image-20220607012040087](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220607012040087.png)

4. C++11以前只有non explicit one argument constructor可以做隐式转化，因此只有这种情况可以使用explicit。但是C++11以后多个参数（argument）的构造函数也可以隐式转化，因此**对多个参数的构造函数也需要允许指定explicit**。

5. 对explict的测试如图下所示，我的理解：

   * 在定义时如果指定了类型，如`P p1{1}`，`fp(P {1,1})`

     * 如果有接受initializer_list的构造函数，那么会优先作为initializer_list传入，此时参数个数不重要

       <img src="https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220607020031755.png" alt="image-20220607020031755" style="zoom:50%;" />

     * 如果没有接受initializer_list的构造函数，那么就会将`{}`里的元素拆出来一个一个传入。如果参数个数不匹配，那就构造失败，报下图注释中的错误。但是**explicit的构造函数会执行**

       <img src="https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220607015925896.png" alt="image-20220607015925896" style="zoom:50%;" />

   * 如果定义时未指定类型，如`P p4 = {77, 5}`, `fp({47, 11})`

     * 如果有接受initializer_list的构造函数，**教案中的错误在MinGW 6.0下并不会发生**，反而都会调用这个接受initializer_list的构造函数

     * 如果没有接受initializer_list的构造函数，那么就会将`{}`中的元素拆成多个传入。**但是因为没有指定类型，因此需要隐式转化，不成立**

       ![image-20220607021045517](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220607021045517.png)

![，image-20220607012640240](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220607012640240.png)