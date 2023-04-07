# Promise
## 异步编程
- fs文件操作
    ```js
    require('fs').readFile('./index.html',(err,data)=>{})
    ```
- 数据库操作
- AJAX
    ```js
    $.get('/server',(data)=>{})
    ```
- 定时器
    ```js
    setTimeout(()=>{},2000)
    ```

## promise流程
启动异步任务-返回promise对象-给promise对象绑定回调函数

## Promise的状态
实例对象中的一个属性 `[[PromiseState]]`，有三种状态，分别是
- pending 未决定的
- resolved/fullfilled 成功
- rejected 失败

## Promise对象的值
实例对象中的一个属性 `[[PromiseResult]]`，保存着异步任务[成功/失败]的结果，

## API
### Promise构造函数 `Promise(excutor){}`
    1. executor函数：执行器 (resolve, reject)=>{}
    2. resolve函数：内部定义成功时调用的函数 value=>{}
    3. reject函数：内部定义失败时调用的函数 reason=>{}
executor会在Promise内部立即同步调用，

### Promise.prototype.then `(onResolved, onRejected)=>{}`
    1. onResolved函数：成功的回调函数 (value)=>{}
    2. onRejected函数：失败的回调函数 (reason)=>{}
    3. 返回一个新的promise对象

### Promise.prototype.catch `(onRejected)=>{}`
    1. onRejected函数：失败的回调函数 (reason)=>{}
    2. obj.catch(onRejected)其实在内部调用obj.then(undefined, onRejected)
    3. 返回一个新的promise对象
    4. 除非onRejected函数抛出一个错误或返回一个本身失败的Promise，则通过catch()返回的Promise实例为rejected；否则返回的Promise实例为resolved

```javascript
let p1 = Promise.resolve('calling next');

let p2 = p1.catch(reason => {
  console.log('catch p1!');
  console.log(reason);
});

p2.then(value => {
  console.log("next promise's onFulfilled");//会走这里
  console.log(value);
}, reason => {
  console.log("next promise's onRejected");
  console.log(reason);
})
```

### Promise.resolve(value)
- 返回一个成功/失败的promise对象 
- value为非promise类型的对象，则返回结果为成功promise对象
- value为promise对象,则返回结果决定了resolve的结果
- value为thenable对象,即带有then方法
```javascript
let p1 = Promise.resolve(new Promise((resolve, reject) => {
    reject('Error');
}));
p1.then(value => {
    console.log(value);
}, reason => {
    console.log(reason);//走这个
})
```

### Promise.reject(reason)
- 返回一个失败的promise对象
- reason是成功的promise对象,返回结果也为失败的promise对象

### Promise.all(iterable)
- iterable是一个可迭代对象,如Array,Map,Set
- 返回一个新的promise,只有所有promise都成功才成功,只要有一个失败就直接失败
- Promise.all获得的成功结果的数组里面的数据顺序和Promise.all接收到的数组顺序是一致的

### promise指定多个成功/失败回调函数，都会调用吗？
只要promise改变为对应状态时都会调用

### 在使用Promise时，在本轮事件循环运行完成之前，回调函数是不会被调用的
### 


## Mac APP
- iWork全家桶+Xcode
- Grapher 
- GeoGebra 几何画板
- AppCleaner
- Clean my mac X
- HomeBrew 包管理工具
- iTerm2
- Go2Shell 文件下快速打开终端
- Sublime Text3
- Postman 接口测试工具
- Charles 抓包神器
- iTerm2 终端
- Navicat Permium 数据库图像化界面
- DataGrip 数据库工具？
- SnippetsLab 代码片段管理工具
- CodeKit 前端开发助理工具
- ps插件-cutterman 一键切图
- Dash API文档离线版
- 11111111111
- magnet
- cleanShot X
- xScope
- iText