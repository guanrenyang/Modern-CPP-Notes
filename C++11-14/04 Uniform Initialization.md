## Uniform Initialization

1. 在变量的后面直接放大括号表示设初值

![image-20220531104123720](https://michael-picgo.obs.cn-east-3.myhuaweicloud.com/image-20220531104123720.png)

黄色的部分就是`initializer_list<T>`，它关联到一个`array<T, n>`，T是类型，n就是参数的个数。调用函数时这个Array里的值会一个一个拿出来传给函数。

构造函数又很多个，如果既有接受其他参数的，也有接受的一个`initializer_list<T>`的，那么就会整个传过去。如果没有接收`initializer_list<T>`的构造函数，编译器就会把他们拆解开一个一个地调用。但是如果只提供了一个接受`initializer_list<T>`的函数，那么调用者必须显示声明一个`initializer_list<T>`，而不能认为给一个`{}`就会被自动打包为`initializer_list<T>`

比如`vector<string>`有一个接受`initializer_list<T>`的构造函数（所有的容器都有一个这样的构造函数），所以会把一包都传过去。而`complex<double>`没有接收一包的构造函数，所以需要将`{}`拆分开来一个一个传。



