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

![](https://github.com/lnn520/picture-blog/blob/main/dom%20(3).png)

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
