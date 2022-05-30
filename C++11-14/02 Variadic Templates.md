# Variadic Templates

1. `...`成为了关键字的一部分，表示可以接受任意变化个数的东西
2. `...`被用来表示一个pack

![image-20220529235733054](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220529235733054.png)

3. 传进来的args的**个数**和**类型**都任意，要告诉模板Type是任意多个：`typename...`
4. Variadic Templates表示数量不定的模板参数
5. 使用Variadic Templates可以用来辅助做递归操作
6. 如上图，进行参数递归一定要有处理无参数版本的函数
7. 在variadic templates里面，`sizeof...(args)`返回pack的个数
8. pack
   1. typename...模板参数包
   2. Types&... 模板参数类型包
   3. args... 函数参数包
9. `template <typename T, typename... Types>` 和 `template<typename... Types>`可以并存，但是有泛化和特化的关系，前者是后者的特化

![image-20220530000918050](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220530000918050.png)

`hash_val`的参数类型不符合2和3，所以会调用到1。1中加入了seed以后会适合于2的特化

10. 可以方便地完成recursive inheritance

![image-20220530001659637](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220530001659637.png)

***使用Variadic Template可以很好地做出Tuple***，Tuple就是任意类型的元素组合起来的对象，它内部实际上是**递归的继承关系**。