### 如何确定一个对象的原型
 let obj =new object()原型是Object.prototype
 
 let arr =new Arry()原型是Array.prototype
 
 let square =new Square()原型是Square.prototype
 
 new X()自动做
 
 1. 自动创建空对象
 2. 自动为空对象关联原型，原型地址为X.prototype
 3. 自动将空对象作为this关键字运行构造函数
 4. 自动return this
 
 
 # 原型公式
 
 对象.__proto__ === 其构造函数.prototype
 
 
 
 # js数组
 
 JS的数组不是典型数组
  
  ## 典型数组元素
  
  * 元素的数据类型相同
  * 使用连续的存储
  * 通过数字下标获取元素
  
  ## JS的数组
  
  * 元素类型可以不同
  * 内存不一定是连续的
  * 不能通过数字下标，而是通过字符串下标
  * 这意味着数组可以有任何key
  
  
  ### 创建一个数组
  
  新建
  
  let arr =[1,2,3]
  
  let arr = new Array(1,2,3)
  
  let arr new Array(3)
  
  
  转化
  
  let arr = '1,2,3'.split(',') 用逗号分隔为一个字符数组
  
  let arr = '123'.split('')
  
  Array.from('123')
  
  
  伪数组
  
  let divList = cocument.querySelectorAll('All')
  伪数组的原型链中并没有数组的yuanxing
  
  
  ### 合并一个数组
  
  arr1.concat(arr2)
  
  截取一个数组的一部分
  
  arr1.slice(1)//从第二个元素开始
  
  arr1.slice(0)//全部截取
  
  注意，JS只提供浅拷贝
  
  
  # 增删改查
  
    ## 删除元素
    
    let arr =a['a','b','c']
    
    delete arr['0'] 数组长度不变
    
    直接修改arr.length可以修改数组长度（不建议使用）
    
   arr.shift()//arr被修改，并且返回被删除元素
   
   arr.pop()//arr被修改，并且返回被删元素
   
   删除中间元素
   
   arr.splice(index.1)//删除index的一个元素
   
   arr.splice(index,1,'x')//并且在删除位置加’x‘
   
   arr.splice(index,1,'x','y')并且在删除位置添加'x''y'
   
 ### 查看所有元素
 
   查看属性
   
   let arr =[1,2,3,4,5];
   arr.x = 'xxx'
   
   Object.keys(arr)
   
   for(let key in arr){console.log(`${key}:${arr[key]}`)}
   
   #### forEach
   
    function forEach(array,fn)
    {
    for(let i = 0;i<array.length;i++)
      {
          fn(arr[i],i,array)
      }

    }
  
### 添加元素
    
    在尾部添加
    
    arr.push
    
    在头部添加
    
    arr.unshift
    
    在中间添加元素
    
    arr.splice(index,0,'x')//在index处插入'x'
    
    
    反转数组arr.reverse()//修改原数组
    
    自定义顺序：
    
    arr.sort((a,b)+>a-b)取决于a-b的值 -反向  + 顺向
    
    
# 数组变化
![](https://github.com/lnn520/picture-blog/blob/main/%E6%95%B0%E7%BB%84%E5%8F%98%E6%8D%A2.png)
map n变n  fillter n变少

![](https://github.com/lnn520/picture-blog/blob/main/%E6%95%B0%E7%BB%84%E5%8F%98%E5%8C%96%20(4).png)

reduce n变1

![](https://github.com/lnn520/picture-blog/blob/main/%E6%95%B0%E7%BB%84%E5%8F%98%E5%8C%96%20(1).png)

![](https://github.com/lnn520/picture-blog/blob/main/%E6%95%B0%E7%BB%84%E5%8F%98%E5%8C%96%20(3).png)

![](https://github.com/lnn520/picture-blog/blob/main/%E6%95%B0%E7%BB%84%E5%8F%98%E5%8C%96%20(5).png)


![](https://github.com/lnn520/picture-blog/blob/main/%E6%95%B0%E7%BB%84%E5%8F%98%E5%8C%96%20(2).png)

![](https://github.com/lnn520/picture-blog/blob/main/%E6%95%B0%E7%BB%84%E5%8F%98%E5%8C%96%20(6).png)






    
  
  
 
