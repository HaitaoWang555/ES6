
## `let`命令
### ES6 新增了`let`命令，用来声明变量。它的用法类似于`var`，但是所声明的变量，只在`let`命令所在的代码块内有效。

```
  {
    let a = 5;
    var b = 6;
  }
  a // ReferenceError: a is not defined.
  b // 6
```

**`let`声明的变量只在它所在的代码块有效**

#### `for`循环的计数器，就很合适使用let命令。
```
  for (let i = 0; i < 10; i++) {
    // ...
  }

  console.log(i);
  // ReferenceError: i is not defined
```

****

### 不存在变量提升

  与`var`命令不同，`let`所声明的变量一定要在声明后使用
  ```
    // var 的情况
    console.log(foo); // 输出undefined
    var foo = 2;

    // let 的情况
    console.log(bar); // ReferenceError: bar is not defined
    let bar = 2;
  ```

****

### 暂时性死区(TDZ)
  ES6 明确规定，如果区块中存在 `let`和`const`命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。
  ```
    if (true) {
      // TDZ开始
      tmp = 'abc'; // ReferenceError: tmp is not defined
      console.log(tmp);

      let tmp; // TDZ结束
      console.log(tmp); // undefined

      tmp = 123;
      console.log(tmp); // 123
    }
  ```

****

### 不允许重复声明
  `let`不允许在相同作用域内，重复声明同一个变量。
  ```
    // 报错  SyntaxError: Identifier 'a' has already been declared
    function func() {
      let a = 10;
      var a = 1;
    }

    // 报错 SyntaxError: Identifier 'a' has already been declared
    function func() {
      let a = 10;
      let a = 1;
    }
  ```

  ****

## 块级作用域

### 为什么需要块级作用域

  ES5 只有全局作用域和函数作用域，没有块级作用域，这带来很多不合理的场景。

  第一种场景，内层变量可能会覆盖外层变量。
  ```
    var tmp = new Date();

    function f() {
      console.log(tmp); // undefined
      if (false) {
        var tmp = 'hello world'; // 变量提升
      }
    }

    f(); // undefined
  ```
  第二种场景，用来计数的循环变量泄露为全局变量。
  ```
    var s = 'hello';

    for (var i = 0; i < s.length; i++) { // i 变量提升
      console.log(s[i]);
    }

    console.log(i); // 5
  ```

  ****
  
### `ES6`的块级作用域
  let实际上为 JavaScript 新增了块级作用域。
  ```
    function f1() {
      let n = 5;
      if (true) {
        let n = 10;
      }
      console.log(n); // 5
    }
  ```

  ****
  
### 块级作用域与函数声明
  ES6 规定，块级作用域之中，函数声明语句的行为类似于let，在块级作用域之外不可引用。
  考虑到环境导致的行为差异太大，应该避免在块级作用域内声明函数。如果确实需要，也应该写成函数表达式，而不是函数声明语句。
  ```
    // 函数声明语句
    {
      let a = 'secret';
      function f() {
        return a;
      }
    }

    // 函数表达式
    {
      let a = 'secret';
      let f = function () {
        return a;
      };
    }
  ```

  ****

## `const` 命令
  ### `const`声明一个只读的常量。一旦声明，常量的值就不能改变。
  ```
    const PI = 3.1415;
    PI // 3.1415

    PI = 3;
    // TypeError: Assignment to constant variable.
  ```


  ### `const`的作用域与`let`命令相同：只在声明所在的块级作用域内有效,常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用,不可重复声明

  

  ### 本质上`const`保证的，并不是变量的值不得改动，而是变量指向的那个内存地址不得改动

  ****

  ## `ES6` 声明变量的六种方法

  `ES5`有`var`命令和`function`命令。`ES6`新增`let` `const` `import`命令和`class`命令

  