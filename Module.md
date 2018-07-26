## Module 的语法

### 模块功能主要由两个命令构成：export和import

```
var firstName = 'Michael';
var lastName = 'Jackson';
var year = 1958;

export {firstName, lastName, year};
```

### export命令除了输出变量，还可以输出函数或类（class）。

```
export function multiply(x, y) {
  return x * y;
};
```

### export输出的变量就是本来的名字，但是可以使用as关键字重命名

```
function v1() { ... }
function v2() { ... }

export {
  v1 as streamV1,
  v2 as streamV2,
  v2 as streamLatestVersion
};

// 上面代码使用as关键字，重命名了函数v1和v2的对外接口。重命名后，v2可以用不同的名字输出两次
```

### export语句输出的接口，与其对应的值是动态绑定关系，即通过该接口，可以取到模块内部实时的值。

```
export var foo = 'bar';
setTimeout(() => foo = 'baz', 500);
// 上面代码输出变量foo，值为bar，500 毫秒之后变成baz。
```

### export命令定义了模块的对外接口以后，其他 JS 文件就可以通过import命令加载这个模块

```
import {firstName, lastName, year} from './xxx';
```

### 输入的变量重新取一个名字，import命令要使用as关键字，将输入的变量重命名

```
import { lastName as surname } from './xxx';
```

### import命令具有提升效果，会提升到整个模块的头部，首先执行

### export default 命令 为模块指定默认输出

```
// export-default.js
export default function () {
  console.log('foo');
}

// import-default.js
import customName from './export-default';
customName(); // 'foo'
```
### 浏览器加载 ES6 模块，也使用`<script>`标签，但是要加入`type="module"`属性。
  ```
  <script type="module" src="./foo.js"></script>
  ```