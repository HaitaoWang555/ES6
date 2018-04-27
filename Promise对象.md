## Promise 是异步编程的一种解决方案
Promise实例生成以后，可以用then方法分别指定resolved状态和rejected状态的回调函数
```
promise.then(function(value) {
  // success
}, function(error) {
  // failure
});
```

