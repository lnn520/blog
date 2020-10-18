# AJAX
## 背景
* AJAX是浏览器的功能
* 浏览器可以发送请求，接收响应
* 浏览器在windows上加了一个XMLHttpRequest函数
* 用这个构造函数可以构造出一个对象
* JS通过它实现发亲求，收响应

# 关于用AJAX加载css  js html  xml json代码在我的另一个仓库

# JSON不是编程语言是标记语言

## 支持的数据类型
* string 只支持双引号，不支持单引号和无引号
* number-支持科学计数法
* bool -true和false
* null -没有undefined
* object
* array
* 就这六种，注意跟JS的七中数据区别开来
* 不支持函数，不支持变量（所以不支持引用）

## window.JSON
### JSON.parse
* 将符合JSON语法的字符串转换成JS对应类型的数据
* JSON字符串=>JS数据
* 由于JSON只有六种类型，所以转成的数据只有六种
* 如果不符合JSON语法，则直接抛出一个ERROR对象
* 一般使用try catch捕获错误
### JSON.stringify
* 是JSON.parse的逆运算
* JS数据=》JSON字符串
* 由于JS的数据类型比JSON多，所以不一定能成功
* 如果失败，就抛出一个ERROR

# 异步 与Promise
 ## 如果能直接拿到结果那就是同步
 ## 如果不能直接拿到结果就是异步 （轮询）（回调）
# 异步举例

* 以AJAX为例
* request.send()之后，并不能直接得到response
* 不信console.log(request.response)试试
* 必须等到readyState变4，浏览器回头调用request.onreadystatechange函数
* 我们才能得到request.response
## 回调callbackk
* 你写给自己用的函数，不是回调
* 你写给别人用的函数，就是回调

## 异步和回调的关系
### 关联
* 异步任务需要在得到结果时通知JS拿结果
* 怎么通知呢
* 可以让JS留一个函数地址给浏览器
* 异步任务完成时浏览器调用该地址即可
* 同时把结果作为参数传给该函数
* 这个函数时我写个浏览器调用的，所以是回调函数
#### 区别
* 异步任务需要用到回调函数通知结果
* 但回调函数不一定只用在异步任务里
* 回调可以用到同步任务里
* array.forEach(n=>console.log(n))就是同步回调

## 怎么判断一个函数是同步还是异步/
* 如果一个函数的返回值处于setTimeout AJAXEventListener AJAX(即：XMLHttpRequest) 这三个东西内部，那么这个函数就是异步函数
还有一些其他的，，，，，

#### 注意：AJAX可以设置为同步的，但是不建议这么做，因为这样会使请求在请求期间使页面卡住

# 2 如果异步任务有两个结果成功或失败，怎么办

## 方法一,回调接受两个参数
## 方法二搞两个回调

### 这些方法的不足
* 不管是方法一还是方法二都有问题
1 不规范，名称五花八门，有人用success+error 有人用success+fail,有人用done+fail
2 容易出现回调地狱，代码变得看不懂
3 很难进行错误处理

# 怎么解决回调问题
我们使用Promise  https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise
## return 呢哇Promise((resolve,reject)=>{})利用这个就可以

### 第一步
* return new Promise((resolve,reject)=>{})
* 任务成功则调用resolve(resule)
* 任务失败则调用reject(error)
* resolve和reject会再去调用成功函数和失败函数
### 第二步
 使用.then(success,fail)传入成功函数和失败函数
 
 # 3 jQuery.ajax
 进入jQuery的文档，搜索ajax,找到jQuery.ajax，看看参数说明，然后直接看代码示例
 链接https://www.jquery123.com/
 
 # 4 axios http://www.axios-js.com/zh-cn/docs/
 
 ## 目前最新的AJAX库
 * 虽然它抄袭了jQuery的封装思路//https://juejin.im/post/6844903569745788941
 ### axios高级用法
 JSON自动处理
 * axios如何发现响应的Content-Type是json
 * 就会自动调用JSON.parse
 * 所以说正确设置Content-Type是好习惯
 ### 请求拦截器
 你可以在所有请求里加东西，比如加查询参数
 ### 响应拦截器
 * 你可以在所有响应里加东西甚至改内容
 
 
