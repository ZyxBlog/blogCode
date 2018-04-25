---
title: js实现侧边栏效果展示
date: 2017-01-02 14:12:48
tags:
- js
categories:
- 前端
---

### html
```bash
<div id="sidebar">    
    <ul>      
        <li class="item" id="prof">       
            <span class="glyphicon glyphicon-user"></span>        
            <div>我</div>      
        </li>      
        <li class="item" id="asset">        
            <span class="glyphicon glyphicon-usd"></span>        
            <div>资产</div>      
        </li>      
        <li class="item" id="brand">        
            <span class="glyphicon glyphicon-heart"></span>        
            <div>品牌</div>      
        </li>      
        <li class="item" id="broadcast">        
            <span class="glyphicon glyphicon-phone-alt"></span>      
            <div>提示</div>      
        </li>      
        <li class="item" id="foot">        
            <span class="glyphicon glyphicon-eye-open"></span>        
            <div>看过</div>      
        </li>      
        <li class="item" id="calendar">        
            <span class="glyphicon glyphicon-time"></span>        
            <div>日历</div>      
        </li>    
    </ul>    
    <div id="closeBar">      
        <span class="glyphicon glyphicon-remove"></span>    
    </div>  
</div>  
<div class="nav-content" id="prof-content">    
    <div class="nav-con-close">      
        <span class="glyphicon glyphicon-chevron-left"></span>    
        <div>我</div>  
    </div>  
    <div class="nav-content" id="asset-content">    
        <div class="nav-con-close">      
            <span class="glyphicon glyphicon-chevron-left"></span>    
            <div>资产</div>  
        </div>  
    <div class="nav-content" id="brand-content">    
        <div class="nav-con-close">      
            <span class="glyphicon glyphicon-chevron-left"></span>       
            <div>品牌</div>  
        </div>  
        <div class="nav-content" id="broadcast-content">    
        <div class="nav-con-close">      
            <span class="glyphicon glyphicon-chevron-left"></span>    
            <div>提示</div>  
        </div>
        <div class="nav-content" id="foot-content">    
            <div class="nav-con-close">      
                <span class="glyphicon glyphicon-chevron-left"></span>    
            </div>    
        <div>看过</div>  
        </div>  
        <div class="nav-content" id="calendar-content">    
            <div class="nav-con-close">      
                <span class="glyphicon glyphicon-chevron-left">    
            </div>    
            <div>日期</div>  
        </div>
    </div>
</div>
```

### css
```bash
body,html{  
    padding:0px;
    margin:0px;
}
ul{  
    list-style: none;  
    padding-left: 0;
}
#sidebar{  
    width:35px;  
    background-color:#e1e1e1;  
    padding-top:200px;  
    position: fixed;  
    min-height:100%;  
    z-index: 100;
}
.item{  
    font-size:12px;  
    font-family: 'Microsoft YaHei';  
    text-align: center;  
    margin-top: 5px;
}
#closeBar{  
    position:absolute;
    bottom:30px;  width:35px;  
    text-align: center;  
    cursor:pointer;
}
.nav-content{  
    width:200px;  
    position:fixed;  
    min-height:100%;  
    background-color:#e1e1e1;  
    border:1px solid black;  
    z-index: 99;  
    opacity: 0;  
    filter:alpha(opacity=0);
}
.nav-con-close{  
    position:absolute;  
    top:5px;  
    right:5px;  
    cursor:pointer;
}
/*********过度:transition*******/
/*********动画:animations*******/
/*********变形transform,translate*********/
.sidebar-move-left{  
    animation-name:smf;  
    -webkit-animation-name:smf;  
    -moz-animation-name:smf;  
    -o-animation-name:smf;  
    animation-duration: 1s;  
    -webkit-animation-duration:1s;  
    -moz-animation-duration:1s;  
    -o-animation-duration:1s;  
    animation-iteration-count:1;  
    -webkit-animation-iteration-count:1;  
    -moz-animation-iteration-count:1;  
    -o-animation-iteration-count:1;  
    /***保持执行后的位置***/  
    -webkit-animation-fill-mode:forwards;  
    animation-fill-mode:forwards;  
    -moz-animation-fill-mode:forwards;  
    -o-animation-fill-mode:forwards;
}
@-webkit-keyframes smf{  
    from{}  
    to{    
        -webkit-transform:translateX(-120px);            
        transform:translateX(-120px);  
    }
}
@keyframes smf{  
    from{  }  
    to{    
        -webkit-transform:translateX(-120px);            
        transform:translateX(-120px);  
    }
}
.closebar-move-right{  
    animation-name: cmr;  
    -webkit-animation-name: cmr;  
    -moz-animation-name:cmr;  
    -o-animation-name: cmr;  
    animation-duration: 1s;  
    -webkit-animation-duration:1s;  
    -moz-animation-duration:1s;  
    -o-animation-duration:1s;  
    animation-iteration-count:1;  
    -webkit-animation-iteration-count:1;  
    -moz-animation-iteration-count:1;  
    -o-animation-iteration-count:1;  
    /***保持执行后的位置***/  
    -webkit-animation-fill-mode:forwards;  
    animation-fill-mode:forwards;  
    -moz-animation-fill-mode:forwards;  
    -o-animation-fill-mode:forwards;  
  }  
  @-webkit-keyframes cmr{    
      from{    }    
      to{      
          -webkit-transform:translateX(160px) rotate(405deg) scale(1.5);              
          transform:translateX(160px) rotate(405deg) scale(1.5);    
      }  
  }  
  @keyframes cmr{    
      from{    }    
      to{      
          -webkit-transform:translateX(160px) rotate(405deg) scale(1.5);              
          transform:translateX(160px) rotate(405deg) scale(1.5);    
        }  
  }  
  ...省略部分代码...
```  

### js面向对象
```bash
(function(){      //块   
    var Menubar = function(){     
        this.el = document.querySelector('#sidebar ul');     
        this.state = 'allClosed';     //初始状态是关闭的     
        this.el.addEventListener('click',function(e){        
            e.stopPropagation();     //阻止时间向上冒泡传播,这样点击菜单项,只响应菜单事件,不干扰sidebar     
        });     
        var self = this;     
        this.currentOpenMenu = null;     
        this.menulist = document.querySelectorAll("#sidebar ul>li");     
        for(var i = 0;i < this.menulist.length; i++) {            
            this.menulist[i].addEventListener('click',function(e) {          
                var menuContentEl = document.getElementById(e.currentTarget.id+'-content');          
                if (self.state === "allClosed") {           
                    console.log('打开'+menuContentEl.id);            
                    menuContentEl.style.top = '0';            
                    menuContentEl.style.left = '-85px';            
                    menuContentEl.className = 'nav-content';            
                    menuContentEl.classList.add('menuContent-move-right');            
                    self.state = "hasOpened";            
                    self.currentOpenMenu = menuContentEl;          
                } else {            
                    console.log('关闭'+self.currentOpenMenu.id);            
                    self.currentOpenMenu.style.top = '0';            
                    self.currentOpenMenu.style.left = '35px';            
                    self.currentOpenMenu.className = 'nav-content';            
                    self.currentOpenMenu.classList.add('menuContent-move-left');            
                    console.log('打开'+menuContentEl.id);            
                    menuContentEl.className = 'nav-content';            
                    menuContentEl.style.top = '250px';            
                    menuContentEl.style.left = '35px';            
                    menuContentEl.classList.add('menuContent-move-up');            
                    self.state = "hasOpened";            
                    self.currentOpenMenu = menuContentEl;          
                }       
          });     
    }     
    this.menuContentList = document.querySelectorAll('.nav-content > div.nav-con-close');     
    for(i = 0;i < this.menuContentList.length; i++) {       
        this.menuContentList[i].addEventListener('click',function(e){         
            var menuContent = e.currentTarget.parentNode;         
            menuContent.style.top = '0';         
            menuContent.style.left = '35px';         
            menuContent.className = 'nav-content';         
            menuContent.classList.add('menuContent-move-left');         
            self.state = "allClosed";       
        });     
    }   
};   
var Sidebar = function(eId,closeBarId) {    //构造函数实例化,注意首字母大写     
    this.state = 'opened';     
    this.el = document.getElementById(eId||'sidebar');     
    this.closeBarEl = document.getElementById(closeBarId||'closeBar');     
    var self = this;     
    this.Menubar = new Menubar();       //生成Menubar实例     
    this.el.addEventListener('click',function(event){       
        if(event.target !==  self.el){     //阻止点击#sidebar任何一处,都触发事件         
            self.triggerSwitch();       
        }     
    });   
};   
Sidebar.prototype.close = function() {      
    console.log("关闭side");      
    this.el.style.left = '0px';      
    this.closeBarEl.style.left = '40px';      
    this.el.className = "sidebar-move-left";      
    this.closeBarEl.className = "closebar-move-right";      
    this.state = "closed";   
};   
Sidebar.prototype.open = function(){      
    console.log("打开side");      
    this.el.style.left = '-120px';      
    this.closeBarEl.style.left = '160px';      
    this.el.className = "sidebar-move-right";      
    this.closeBarEl.className = "closebar-move-left";      
    this.state = "opened";   
};   
Sidebar.prototype.triggerSwitch = function() {     
    if(this.state === "opened") {       
        this.close();     
    } else {       
        this.open();     
    }   
};   
var sidebar = new Sidebar();
```

### output
![show](http://oj171eydn.bkt.clouddn.com/slider.png)
