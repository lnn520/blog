# 网页其实是一棵树

![](https://github.com/lnn520/picture-blog/blob/main/dom%20(3).png)

### js用documentt操作网页

## 获取元素，也叫标签

* 有很多api
* window.idxxx或者idxxx
* document.getElementById('idxxx')
* document.getElementsBytagName('div')[0]
* document.getElenemtsByClassName('red')[0]
* document.querySelector('#idxxx')
* document.querySelectorAll('.red')[0]

用哪一个
基本使用querySelevtor和querySelectorAll

## 获取特定元素
* 获取html元素
* document.documentElement
* 获取head元素
* document.body
* 获取body元素
* document.body
* 获取窗口（窗口不是元素）
* window
* 获取所有元素
* document.all
* 这个是第六个falsy


# 获取的元素到底是个啥
* console.dir(div1)看原型链
* 自身属性:className,id,style等等
* 第一层原型HTMLDivElement.prototype
* 这里面是所有div共有属性
* 第二层原型HTMLElement.prototype
* 这里面是HTML标签的共有属性
* 第三层原型Element.prototype
* 这里面是所有XMl,XHTML标签的共有属性
* 第四层原型Node.pototype
* 这里面是所有结点的共有属性，节点包括XML标签文本注释，HTML标签文本注释等
等
* 第五层原型EventTarget.prototype
* 里面最重要的函数就是addEventListener
* 最后一层原型就是Object.prototype

![](https://github.com/lnn520/picture-blog/blob/main/dom%20(4).png)

# 节点？元素？
### 节点Node包括一下几种
* MDN有完整描述，x.nodeType得到一个数字
* 1表示元素Element,也叫标签Tag
* 2表示文本Text
* 8表示注释Comment
* 9表示文档Document
* 11表示文档片段Document
* 记住1,2即可

## 节点的增删改查
### 增
#### 创建一个节点
* let div1 =document.createElenent('div')
* document.createElement('style')
* document.createElement('script')
* document.createElement('li')
#### 创建一个文本节点
* text1 = document.createTextNode('你好')
#### 标签里插入文本
* div1.appendChild(text)
* div1.innerText='你好'或者div1.textCount = '你好'
* 但是不能使用div1.appendChild('你好')
#### 插入页面中
* 你创建的标签默认处于JS线程中
* 你必须把它插入到head或者body里面，它才会生效
* document.body.appendChild(div)
* 或者已在页面中的元素.appendChild(div)
### 删
#### 两种方法
* 旧方法:parentNode.childChild(childNode)
* 新方法:childNode.remove()
### 改属性
#### 写标准属性
* 改class:div.className = 'red blue'(全覆盖)
* 改class:div.classList.add('red')
* 改style:div.style = 'width:100px;color:blue;'
* 改style的一部分:div.style.backgroundColor:='while'
* 改data-*属性：div.dataset.x='mmy'
#### 读标准属性
* div.classList/a.herf
* div.getAttribute('class')/a.getAttribute('href')
* 两种方法都可以，但值可能稍微有些不同
### 改事件处理函数
* div.onclick默认为NUll
* 默认点击div不会有任何事情发生
* 但是如果你把div.onclick改为一个函数
* 并且是这样调用的fn.call(div,event)
* div会被当做this
* event则包含了时间点击的所有信息，如，坐标
* div.addEventListener
* 是div.onclick的升级版
### 改内容
#### 该文本内容
* div.innerText ='sss'
* div.textCountent = 'xxx'
* 两者几乎没有区别
#### 改HTML内容
* div.innerHtML = '<strong>重要内容</strong>'
#### 改标签
* div.innerHTML = ''//先清空
* div.appendChild(div2)//再加内容
### 改爸爸
* newParent.appendChild(div)//直接这样就可以了，直接在原来的地方消失

###查
#### 查爸爸
* node.parentNode或者node.parentElement
#### 查爷爷
* node.parentNode.parent.Node
#### 查子代
* node.childNodes或者node.children
#### 查兄弟姐妹
* node.parentNode.childNode
* node.oarentNode.children
* 还要排除自己
#### 查看老大
* node.firstChild
#### 查看最后一个子元素
* node.lastChild
#### 查看上一个哥哥
* node.previousSibliing
#### 查看下一个妹妹
* node.nextSibling
# DDM操作时跨线程的
* 浏览器分为渲染引擎和JS引擎
### 跨线程操作
#### 各线程各司其职
* JS引擎不能操作页面，只能操作JS
* 渲染引擎不能操作JS,只能操作页面
* document.body.appChild(div1)
* 这句JS只如何改变页面的？
#### 跨线程通信
* 当浏览器发现JS在body里面加了个div1对象
* 浏览器就会通知渲染引擎在页面里也新增一个div元素
* 新增的div元素所有属性都照抄div1对象
#### 图示跨线程操作
![](https://github.com/lnn520/picture-blog/blob/main/dom%20(2).png)

### 插入新标签的完整过程
#### 在div1放入页面之前
* 你对div1所有的操作都属于JS线程的操作
#### 把div1放入页面之时
* 浏览器会发现JS的意图
* 就会通知渲染线程在页面中渲染div1对应的元素
#### 把div1放入页面之后
* 你对div1的操作都有可能会触发重新渲染
* div1.id = 'newId'可能会重新渲染，也可能不会
* div1.title = 'new'可能会重新渲染，也可能不会
* 如果你连续对div1多次操作，浏览器可能会合并成一个操作，也可能不会
## 属性同步
#### 标准属性
* 对div1的标准属性的修改，会被浏览器同步到页面中
* 比如id,className,title
#### data-*属性
* 同上
#### 非标准属性
* 对非标准属性的修改，则只会停留在JS线程中
不会同步到代码
* 比如你添加了 xxx属性
#### 启示
* 如果你有自定义的属性，又想被同步到页面中，请使用data-作为前缀
### 图示
![](https://github.com/lnn520/picture-blog/blob/main/dom%20(1).png)

# propertyv.s.Attribute
### property属性
* JS线程中DIV1的所有属性，叫做div1的property
### attribute也是属性
* 渲染引擎中div1对应标签属性，叫做attribute
### 区别
* 大部分时候，同名的property和attribute值相等
* 但如果不是标准属性，那么它两只会在一开始时相等
* 但注意attribute只支持字符串
* 而property支持字符串，布尔等类型
