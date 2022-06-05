# Initializer List

1. Initializer List的实现原理比较复杂，对标准库影响也很大，因为它接受**可变的参数**
2. ![image-20220605140735695](C:/Users/69540/AppData/Roaming/Typora/typora-user-images/image-20220605140735695.png)

3. 如果大括号内的东西和变量的类型不一样，**编译器是不允许narrow conversion**。（有的编译器是warning）

   ![image-20220605141206769](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220605141206769.png)

4. 初始化列表背后是一个类：`std::initializer_list<>`
5. 当函数声明中的参数是initializer_list，调用者就可以传入一个`{}`![image-20220605143307467](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220605143307467.png)

这是一个参数个数不定的列表。不定参数列表更厉害，它可以接受不同类型的参数。

6. 第一个(77, 5)调用第一个函数；第二个{77,5}形成一包；第三个{}形成一包，此时可以接受任意个数个参数 ；第四个不会调用操作符重载，而是会调用构造函数。

   如果没有接受initializer的构造函数，那么编译器会把{}里的拆解开，对于第二个函数，编译器会将{}的拆开为两个参数，并找到一个接受两个参数的构造函数；对于第三个情况，就调用失败了。

   ![image-20220605152902733](C:/Users/69540/AppData/Roaming/Typora/typora-user-images/image-20220605152902733.png)

   

7. initializer_list背后有一个array在支撑，但是initializer并没有内涵一个array对象，而是使用一个类似于array构造函数的函数来分配内存。initializer_list内部没有array对象，而**只有一个指针**。

8. 当initializer_list进行拷贝时，会拷贝指针，造成两个指针指向同一个数组的情况。

9. initializer_list对标准库的影响：现在stl中的容器都支持可变长初始化。

10. 使用{}可以进行**任意多个元素比min、max**（以前只能一次比两个）

    ![image-20220605154942119](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220605154942119.png)

11. 容器举例：vector的初始化可以有以下三种方式。

    ![image-20220605154824883](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220605154824883.png)