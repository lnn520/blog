# js 运算符

![](https://github.com/lnn520/picture-blog/blob/main/js%E6%80%BB%E7%BB%93%20(1).png)

![](https://github.com/lnn520/picture-blog/blob/main/js%E6%80%BB%E7%BB%93%20(2).png)

![](https://github.com/lnn520/picture-blog/blob/main/js%E6%80%BB%E7%BB%93%20(3).png)

![](https://github.com/lnn520/picture-blog/blob/main/js%E6%80%BB%E7%BB%93%20(4).png)

### 特例 NaN != NaN

## 布尔运算符

或且非

||  &&  !

短路逻辑

console&&console.log&&console.log('hi')

以防ocnsole不存在报错


a = a || 100

a 的保底值 但是 a 为空字符串有问题

## 可以使用移位运算来取整

例子：

  使用^来交换a,b的值
  
  代码
    
    var a = 5
    
    var b = 8
    
    a ^= b
    
    b ^= a
    
    a ^= b
    
    console.log(a)
    
    console.log(b)
    
# 点运算符 

  语法
  
  对象.属性名  = 属性值
  
  作用
  
  读出对象的属性值
  
  问题“
  
  不是对象，为什么也可以有属性？ 'a-b-c'.split('-')
  
  js有特殊逻辑，点前面不是对象，就把它转化为对象
  
# void 

 
    
    
