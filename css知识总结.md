# 浏览器的渲染原理
  ![tu](https://github.com/lnn520/picture-blog/blob/main/%E6%B5%8F%E8%A7%88%E5%99%A8%E7%9A%84%E6%B8%B2%E6%9F%93%E8%BF%87%E7%A8%8B.png)
  
  有三棵树见下图
  
  ![](https://github.com/lnn520/picture-blog/blob/main/%E4%B8%89%E6%A3%B5%E6%A0%91.png)
  
  
  我们一般使用js来更新样式
    比如div.style.background='red'
    
 ## 三种更新方式
    
    1. JS/CSS>样式>布局>绘制>合成  
    2. JS/CSS>样式>绘制>合成
    3. JS/CSS>样式>合成  
    
    如图
    ![](https://github.com/lnn520/picture-blog/blob/main/%E4%B8%89%E7%A7%8D%E6%9B%B4%E6%96%B0%E6%96%B9%E5%BC%8F.png)
 
# 两种红心制作

Css代码
        *{box-sizing: border-box;}
    #heart{
        display: inline-block;
        margin: 100px;
        position: relative;
        transition: all 1s;

    }
    #heart:hover{
        transform: scale(1.2);

    }

    #heart>.left{
        background: red;
        width: 50px;
        height: 50px;
        position: absolute;
        transform: rotate(45deg) translateX(31px);
        bottom: 50px;
        left: -50px;
        border-radius: 50% 0 0 50%;
    }
    #heart>.right{
        background: red;
        width: 50px;
        height: 50px;
        border-radius: 50%;
        position: absolute;
        transform: rotate(45deg) translateY(31px);
        bottom: 50px;
        right: -50px;
        border-radius: 50% 50% 0 0;
    }
    #heart>.bottom{
        background: red;
        width: 50px;
        height: 50px;
        transform: rotate(45deg);
    }

第二种
    #heart{
        display: inline-block;
        margin: 100px;
        position: relative;
        animation: .5s heart infinite alternate-reverse;

    }
    @keyframes heart {
        0%{
            transform: scale(1);
        }
        100%{
            transform: scale(1.2);
        }
    }
   只需要修改这一部分就好了
   
   看一下我的截图
   
   
   ![](https://github.com/lnn520/picture-blog/blob/main/%E9%97%AA%E5%8A%A8%E7%9A%84%E7%BA%A2%E5%BF%83.png)
   ![](https://github.com/lnn520/picture-blog/blob/main/%E9%97%AA%E5%8A%A8%E7%9A%84%E7%BA%A2%E5%BF%83%20(2).png)
   
   动画效果在这没办法演示，代码可以拷贝也可以在我的另一个仓库查看。
