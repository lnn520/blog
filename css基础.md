1.css中的文档流
流动方向
inline元素从左到右，到达最右边才会换行
block 元素从上到下，每一个都是另起一行
inline-block也是从左到右
宽度
inline的宽度为内部inline元素的的和,不能用width 指定
block 默认自动计算宽度，可用发width指定
inline-block结合前两者的特点，

高度
inline 高度由line-height间接指定 和height无关
block高度由内部文档流元素决定,可以设置height



overflow溢出

等内容的宽度或高度大于容器的，会溢出
可用 overflow 来设置是否显示滚动条
auto 是灵活设置
scroll 是永远显示
hidden 是直接隐藏溢出部分
visible 是直接显示溢出部分
overflow 可以分为 overflow-x 和 overflow-y

两种盒子模型
分别是
content-box 内容盒 - 内容就是盒子的边界
border-box 边框盒 - 边框才是盒子的边界
公式
content-box width = 内容宽度
border-box width = 内容宽度 + padding + border
哪个好用
border-box 好用
同时指定 padding、width、border 就知道为什么了

margin合并
哪些情况会合并
父子 margin 合并
兄弟 margin 合并
如何阻止合并
父子合并用 padding / border 挡住
父子合并用 overflow: hidden 挡住
父子合并用  display: flex，不知道为什么
兄弟合并是符合预期的
兄弟合并可以用 inline-block 消除
总之要一条一条死记
而且 CSS 的属性逐年增多，每年都可能有新的
