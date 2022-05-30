## Space in template expression

模板表达式中可以出现空格，比如可以`vector<vector<int>>`而不需要`vector<vector<int> >`

## nullptr

1. 可以使用nullptr来取代0和NULL，来指明一个空指针。nullptr的类型是`void*`而`NULL`可能是 `int`

## auto

`auto`允许声明一个变量或对象，而不指明他的类型。当变量类型特别长或是一个复杂的表达式时，很常用。

*不能因为有了`auto`，就全都用`auto`最终导致类型的不明确*

auto可以定义变量，也可以定义lambda函数