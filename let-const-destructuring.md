ES6 新增了`let`命令，用来声明变量。它的用法类似于`var`，但是所声明的变量，只在`let`命令所在的代码块内有效。

```
{
let a = 5;
var b = 6;
}
a // ReferenceError: a is not defined.
b // 6
```





