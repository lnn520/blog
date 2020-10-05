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
  
  
  
    
