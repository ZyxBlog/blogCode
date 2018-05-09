---
title: css实现三个自适应等高
date: 2017-02-18 12:59:53
tags:
- css
categories:
- 前端
---

一开始看这个问题有点懵，仔细想想，可以用table的性质来实现，因为table就是自适应等高的。
### html
```bash
<div class="table">  
    <div class="box">    
        <p>Number1</p>  
    </div>  
    <div class="box">    
        <p>Number2</p>  
    </div>  
    <div class="box">    
        <p>Number3</p>  
    </div>
</div>
```

### css
```bash
html {    
    font-size: 10px;
}
.box {  
    background-color: rgba(200,200,200,0.7);
}
.box:nth-child(2) {  
    background-color: rgba(200,210,230,0.7);
}
.table {    
    width: 100%;    
    display: table;
}
.table  .box {    
    display: table-cell;
}
```

那如果是两栏布局，一边固定，一边是自适应，则：
```bash
#left {
    float: left;  
    width:100px;  
    background: #000;
}
#right {  
    overflow: hidden;  
    background: blue;
}
```
