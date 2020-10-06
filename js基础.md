# Js 语法
  
### 表达式和语句
  
  1+2表达式值为3
  
  add(1,2)表达式的值为函数的返回值
  
  console.log表达式的值为函数本身
  
  console.log(3)表达式的值为多少
  
  unidefine 
  
### 问好冒号表达式
  表达式1？表达式2：表达式3
  
### &&短路逻辑 
  A && B && c && d 取第一个假值或D
    并不会取true/flase
    
### ||短路逻辑
  A || B || C || D
  取第一个真值，并不会取true/false
  
  
##  label语法
  foo:{
    console.log(1);
    break foo;
    console.log('本行不会输出')
      }
    console.log(2)
    
    ..................................
    
    {
    foo: 1
    }
    表示一个label语句结果为1
    
# 数据类型和运算符
  ## js中的数据类型
  
  有7种：
     数字number
     
     字符串：string
     
     布尔bool
     
     符号symbol
     
     空undefined
     
     空null
     
     对象object
     
     总结：四基两空一对象
     
### number
    正0和负0
    
    无法表示的数字
    
    NaN （Not a Number）
    但是它它是一个数字
    
    范围和精度
    
    Number.MAX_VALUE:1.79769313482623157e+308
    Number.MIN_VALIUE:5e-324
    
    精度： 最对表示52+1个二进制位表示有效数字
    
    2^53对应的十进制是9后面15个零
    
    所以15位有效数字都能精确表示
    
    16位有效数字如果小于90开头，也能精确表示
    
### string
    
    单引号
    
    '你好'
    
    双引号
    
    "你好"
    
    反引号
    
    `你好`
    
    注意：引号不属于字符串的一部分，就像书名号不属于书名一样，如果想在单引号加单引号必须加转义字符\
    或者双引号包单引号，反引号包单引号
    
    如果想在字符串里加回车j=可以使用反引号包含字符串
#### 字符串的属性

### boolean
 
 五个falsy值
  
  undefined null 0 NaN ''
  
 NaN 和 undefined 的区别
 ![](https://github.com/lnn520/picture-blog/blob/main/%E7%A9%BA%E7%9A%84%E5%8C%BA%E5%88%AB.png) 
 
### symbol 

https://zhuanlan.zhihu.com/p/22652486

# 变量的声明
                              
                              
  
  
        三种声明方式
        
        var a = 1
        
        let a  = 1
        
        const a = 1
        
        区别：var是过时的不好使用的方式
        
        let是新的，更合理的方式
        
        const是声明必须赋值，且不能改的方式
        
## let声明
  遵循块作用域，使用范围不能超出{}
  
  不能重复声明
  
  可以复制，也可以不赋值
  
  必须声明才能使用，否则报错
  
  全局声明的let变量，不会变成window的属性
  
## const 声明

  跟let几乎一样
  
  只有一条不一样：声明时就要赋值，并且不能改
  
# name 和 'name'的区别
  
  name是变量
  
  值可变，可能是'name',也可能是'hello'
  
  'name'是字符串常量
  
  常量就是不变量
  
  'name'只能是'name',不能是其他值
  
  
## 类型转换

  number => string
  
  n+''
  
  string => number
  
  s - 0
  
  x => bool
  
  !!x
  
  x => string
  
  x.toString()
  
# object 复杂数据类型

定义
  
  无序的数据集合，键值对集合
  
  let obj = {'name':'frank','age':18}
  
  let obj = new Object({'name':'frank'})
  
  consolle.log({'name': 'frank','age':18})
  
 ## 细节：
  键名是字符串，不是标识符，可以包含任何字符
  
  引号可以省略，省略之后只能写标识符
  
  就算引号省略了，键名还是字符串
  
  属性名：每个key都是对象的属性名（property）
  
  属性值：每个value都是对象的属性值
  
  
  Object.keys(obj)可以得到obj的所有key
  
  ## 变量作属性名
  
    如何用变量做属性名
    
    let p1 = 'name'
    
    let obj ={p1:'frank'}这样写，属性名为‘p1’
    
    let obj = {[p1]:'frank'}这样写，属性名为'name'
    
 ## 对象的隐藏属性
 
      JS中每一个对象都有一个隐藏属性
      
        这个隐藏属性存储着其共有属性组成的对象的地址
        
        这个共有属性组成的对象叫做原型
        
        也就是说，隐藏属性存储着圆形的地址
        
        代码示例
          
           var obj = {}
           
           obj.toString()//
           
           因为obj的隐藏属性对应的对象上有toString所以不会报错
 
 
 # 关于对象的增删改查
   delete obj.xxx或delete obj['xxx']
   
   即可删除obj的xxx属性
   
   不含属性名
   
   'xxx' in obj === flase
   
   含有属性名，但是值为undefined
   
   'xxx' in obj&&obj.xxx === undefined
   
   注意obj.xxx === undefined
   
   不能断定'xxx'是否为obj的属性
   
 ## 查看所有属性
 
  查看自生所有属性
  
  Object.keys(obj)
  
  查看自身+共有属性
  
  console.dir(obj)
  
  或者自己依次使用Object.keys打印obj.__proto__
  
  判断一个属性是自身的还是共有的
  
  obj.hasOwnProperty('toString')
  
# 原型
  
##  每个对象都有原型
  
  原型里存着对象的共有属性
  
  比如obj的原型就是一个对象
  
  obj.__proto__存着这个对象的地址
  
  这个对象里有toString/constrctor/valueOf等属性
  
 ## 对象的原型也是对象
  
  所以对象的原型也有原型
  
  obj = {} 的原型极为所有对象的原型
  
  这个原型包含所有对象的共有属性，是对象的根
  
  这个原型也有原型，是null
  
  # 查看属性
    
    两种方法查看属性
    
    中括号法:obj['key']
    
    点语法：obj.key
    
    注意：obj[key]//变量key值一般不是’key‘
    
    优先使用中括号法
 
 ## 修改或增加属性
 
  ### 直接赋值
    
    let obj = {'name':'frank'} //name是字符串
    
    obj.name = 'frank' //name是字符串
    
    obj['name'] = 'frank' 
    
  ### 批量赋值
  
    Object.assign(obj,{age:18,gender:'man'})
    
 ## 修改或增加共有属性
 
  #### 无法通过自生修改或增加共有属性
  
  let obj ={},obj2 = {}//共有toString
  
  obj.toString = 'xxx'只会在改obj自身属性
  
  obj2.toString还是在原型上
  
  
  #### 修改圆形的属性
  
  obj.__proto__.toString =  'xxx' //不推荐使用__proto__
  
  Object.prototype.toString = 'xxx'
  
  一般来说，不要修改原型，会引起很多问题
  
 ### 修改隐藏属性
 
 不推荐使用__proto__
 
 let obj = {name:'frank'}
 
 let obj2 = {name:'jack'}
 
 let common ={kind:'human'}
 
 obj.__proto__ = common
 
 obj2.__proto__ = common
 
    推荐使用OBject.creat
    
    let obj = Object.creat(common)
    
    obj.name = 'frank'
    
        let obj2 = Object.creat(common)
    
    obj2.name = 'jack'
    
# 总结
![](https://github.com/lnn520/picture-blog/blob/main/(RT)2%7D%25KM%5BDHX3EA7VU25EH.png)
![](https://github.com/lnn520/picture-blog/blob/main/2F2P%7BHIZ%7DE%24C7_J%60T(WPB%253.png)
    
    
  
          
  
  



  
  
    
