## Class 类
```
//定义类
class Point {
  constructor(x, y) {
    this.x = x
    this.y = y
  }

  toString() {
    return '(' + this.x + ', ' + this.y + ')'
  }

  sum() {
    return this.x + this.y
  }
}
```
### 函数声明和类声明之间的一个重要区别是函数声明会提升，类声明不会
### constructor方法是一个特殊的方法，其用于创建和初始化使用class创建的一个对象。一个类只能拥有一个名为 “constructor”的特殊方法
### 类的方法内部如果含有this，它默认指向类的实例
### static 关键字用来定义一个类的一个静态方法。调用静态方法不需要实例化该类，但不能通过一个类实例调用静态方法。静态方法通常用于为一个应用程序创建工具函数。
### super 关键字用于调用对象的父对象上的函数。方法内部的this指向当前的子类实例。
### extends 关键字在类声明或类表达式中用于创建一个类作为另一个类的一个子类
```
class Animal { 
  constructor(name) {
    this.name = name
  }

  run() {
    console.log(this.name + ' run')
  }  
  static printName() {
    console.log(this.name)
  }
  speak() {
    console.log(this.name + ' makes a noise.')
  }
}

class Dog extends Animal {+
  constructor(name, age) {
    super(name)
    this.age = age
  }

  sayAge() {
    console.log(this.name + this.age + ' age.')
  }
  
  speak() {
    super.speak()
    console.log(this.name + ' barks.')
  }
}

var d = new Dog('Mitzie', 24)
d.run() // Mitzie run
d.speak() // Mitzie makes a noise. // Mitzie barks.
d.sayAge() // Mitzie24 age.
d.printName() // 报错  d.printName is not a function
Animal.printName() // Animal
```