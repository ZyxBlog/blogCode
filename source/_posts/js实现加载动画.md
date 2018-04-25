---
title: css3实现加载动画
date: 2017-01-10 14:14:03
tags:
- css3
categories:
- 前端
---

### code
```bash
<style type="text/css">     
*{       
    padding:0;       
    margin:0;     
}     
.container{       
    width:60px;       
    height:60px;       
    position:absolute;       
    top:33%;       
    left:50%;     
}     
.container div{      
    width:15px;       
    height:15px;       
    background-color:rgb(25, 240, 33);       
    border-radius:20px;       
    position:absolute;       
    animation:bounce 0.8s infinite;       
    /*****bounce是名字,animation: name duration timing-function delay iteration-count direction;******/     
}     
.circle1{          
    left: 0;          
    top: 0;      
}      
.circle2{          
    right: 0;          
    top: 0;      
}      
.circle3{          
    right: 0;          
    bottom: 0;      
}      
.circle4{          
    left: 0;          
    bottom: 0;      
}      
.container2{          
    transform: rotate(45deg);      
}      
.container1 .circle1{     
/***animation-delay为负值时表示，动画跳过多少秒进入动画周期。***/     
    animation-delay: -0.8s;            
}      
.container2 .circle1{          
    animation-delay: -0.7s;     
}      
.container1 .circle2{        
    animation-delay: -0.6s;        
}      
.container2 .circle2{          
    animation-delay: -0.5s;      
}     
.container1 .circle3{          
    animation-delay: -0.4s;      
}      
.container2 .circle3{          
    animation-delay: -0.3s;      
}      
.container1 .circle4{          
    animation-delay: -0.2s;      
}      
.container2 .circle4{          
    animation-delay: -0.1s;      
}      
@keyframes bounce{          
    0%,100%{transform: scale(0.0);}          
    50%{transform: scale(1.0);}     
}  
</style>
<body>   
    <div class="container container1">     
        <div class="circle1"></div>     
        <div class="circle2"></div>     
        <div class="circle3"></div>     
        <div class="circle4"></div>   
    </div>   
    <div class="container container2">     
        <div class="circle1"></div>     
        <div class="circle2"></div>     
        <div class="circle3"></div>     
        <div class="circle4"></div>  
    </div>
</body>
```
![show](http://oj171eydn.bkt.clouddn.com/loading.png)
![show](http://oj171eydn.bkt.clouddn.com/loading1.png)
