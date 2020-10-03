

# 浏览器的功能

  发起请求，下载html，解析html，下载css，解析css,渲染界面，下载js，解析js,执行js等
  
  功能模块：用户界面，渲染引擎，js引擎，存储等
  
  上面功能处于不同线程
  
## JS引擎

  Chrome用的是引擎，C++编写
  
  网景用的是SPiderMonkey，后被Firefox使用，C++ 
  
  Safari用的是JavaScriCore
  
  ie使用的是Chakra
  
  node.js使用的是v8引擎
  
### 主要功能
  
  编译：把JS代码翻译为机器能执行的字节码或机器码
  优化：改写代码，使其更高效
  执行：执行上面的字节码或者机器码
  垃圾回收：把js用完的内存回收，方便之后再次使用
  
  
# 内存
  堆(heap)和栈（staack）
  
  栈的特点：每个数据顺序存放
  堆的特点：每个数据随机存放
  
 规律：数据分为对象和非对象
      非对象都存在栈，对象存在堆
  
  
 # 图片在本仓库另一个文件里
 ![图片](https://github.com/lnn520/blog/blob/master/%E5%86%85%E5%AD%98%E5%9B%BE.png)
 ![原型图](https://github.com/lnn520/blog/blob/master/%E5%8E%9F%E5%9E%8B%E5%9B%BE.png)
