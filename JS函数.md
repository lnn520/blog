# 函数的要素

  ## 每个函数都有这些东西
  
  调用时机
  
  作用域
  
  闭包 
  
  形式参数
  
  返回值
  
  调用栈
  
  函数提升
  
  arguments(除了箭头函数)
  
  this(除了箭头函数) 
  
  
  ### 闭包
      如果一个函数用到了外部的变量，那么这个函数加这个变量就叫做闭包、
      
  ### 调用栈
  
  js引擎在调用一个函数前需要把函数所在的环境push到一个数组里
  
  这个数组就叫做调用栈
  
  等函数执行完了，就会把环境弹出来，然后return到之前环境，继续执行后续代码
  
  ### 函数提升
  
  不管你把函数声明到哪里，它都会跑到第一行
  
  let fn = function(){}
  这是赋值，右边的匿名函数声明不会提升
  
  
  ## this
  
  js 通过额外的this做到：
  
  person.sayHi()会把person自动传给sayHi，sayHi可以通过this引用person
  
  两种调用：
  
  person.sayhi()
  
  会自动把person传到函数里作为this
  
  
  第二种
  
  person.sayHi.call(person)
  
  需要自己手动把person传到函数里,作为this
  
  例子;
  function add() {
    return x+y;
  }
  
  add.call(undefined,1,2)//3
  
  为什么要多谢一个undefined 
  因为第一个参数要作为this，但是代码里没有this 所以只能用undefined占位
  其实用null也可以
  
