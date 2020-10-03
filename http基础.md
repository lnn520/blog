## 路由器的功能
   ip分内网ip和外网ip
   
   内网的设备可以互相访问，但是不能直接访问外网
   
   内网的设备访问外网就必须通过路由器中转
   
   外网的设备可以互相访问但是不能访问你的内网
   
   外网的设备想要把内容送的内网，也必须通过路由器
   
   内网和外网只有通过路由器才能相通
   
   所以路由器有时也叫网关
## 几个特殊的IP、
  127.0.0.1表示自己
  
  localhost通过hosts指定为自己
  
  0.0.0.0不表示任何设备
  
## 端口port


  一台机器可以提供不同的服务
  
    要提供HTTP最好使用80端口
    
    要提供HTTPS服务最好使用443端口
    
    要提供RTP最好使用21端口
    
    一共有65535个端口
 ### 端口的使用规则
  0到1023号端口是留给系统使用的
  
  你只有获取了管理员权限带能使用这1024个端口
  
  其他端口可以给普通用户使用
  
  比如Http-server默认使用8080端口
  
  一个端口如果被占用，你就只能换一个端口
  
## 域名就是对IP的别称

  baidu.com对应什么IP
  
  qq.com对应什么IP
  
  ping qq.com
  
  知识点
  * 一个域名可以对应不同ip
  
  * 这个就是负载均衡,防止一个机器扛不住
  
  * 一个ip可以对应不同的域名
  
  * 这个叫做共享主机，
  
  
## 域名和I是怎么对应起来的

  当你输入baidu.com时
  
  你的浏览器会向电信或者联通提供的dns服务器询问daifu.com对应什么ip
  
  电信会回答一个ip
  
  然后浏览器才会响应对应ip的80/443端口发送请求
  
  然后内容是查看baidu.com的首页
  
### 为什么是80/443端口

  服务器默认使用80提供http服务
  
  服务器默认使用443tigonghttps服务
  
  你可以在开发者工具里看到具体的端口
  
  
  
# url
   
   协议+域名或ip+端口号+路径+查询字符串+锚点
## curl命令

  用curl命令可以发送http请求
  
  curl -v http://baidu.com
  
  curl -s-v --https://www.baidu.com
  
## 理解一下概念 

url会被curl工具重写，线请求dns获得ip
先进行TCP连接，TCP连接成功后，开始发送HTTP请求


## http请求和响应
  
  如何做出一个响应
   需用编程
   node.js有一个thttp模块可以做到
   初始代码在我另一个写服务器的仓库中
   
   注意事项：
   
      这些代码就是服务器代码，一般放在服务器上
      
      path是不带查询参数路径/x
      
      query是查询参数的对象形式{a:'1'}
      
      querySthing是查询参数字符串形式？a=1
      
      pathWithQuery是带查询参数的路径，一般不用
      
      request是请求对象
      
      response是响应对象
# 代码逻辑
   语法`这种字符串`里面可以回车
   回车只能用\n表示
   
   逻辑
      每次收到请求都会把中间的代码执行一遍
      
      if else 判断路径，并且返回响应
      
      如果是已知路径，一律返回200
      
      如果是未知路径一律返回404
      
      Content-Type表示内容/语法
      
      response.write（）可以填写返回的内容
      
      response.end（）表示响应可以发给用户了
      
      
      注意：url的后缀没有用，Content-Type才是决定文件类型的关键
      
# http基础概念
   响应
      
      协议名/版本 状态码 状态字符串 
      
      Content-Type响应体的格式
      
      回车
      
      响应体（也就是下载内容）
      
    细节
    
      三部分;状态行，响应头，响应体
      常见的状态码是考点
      文档在RFC2612第六章
      
  ## 用curl 构造请求
  
      curl -v http://127.0.0.1:8888
      
      设置请求动词
        -X POST
        注意大小写
      设置路径和查询参数
         直接在URL后面加
       设置请求头
         -H'Name:Value'或者--header'Name:Value'
        设置请求体
        -d'内容'或者--data'内容'
        
  ## 用node.js读取请求
         读取请求动词
         
         request.method
         
         读取路径
         
         reques.url路径，带查询参数
         
         path纯路径，不带查询参数
         
         query只有查询参数
         
         读取请求头
         
         request.headers['Accept']
         
         读取请求体
         
  ## 用node.js读取请求  
      设置响应状态码
      
         response.statusCode= 200
         
       设置响应头
       
       response.setHeader('Content-Type','text/html')
       
       
       设置响应体
       
       response.write(内容)
       可追加内容
       
       
    
  
  


  
