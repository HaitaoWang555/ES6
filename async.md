## async
把异步代码写成同步代码
```
function resolveAfter2Seconds(x) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(x)
    }, 2000)
  })
}

async function add1(x) { 
  var a = await resolveAfter2Seconds(20) 
  var b = await resolveAfter2Seconds(30) 
  return x + a + b 
}
 
add1(10).then(v => { 
  console.log(v) // prints 60 after 4 seconds. 
})
```
