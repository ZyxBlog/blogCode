---
title: jquery封装打字效果的插件
date: 2016-10-28 10:35:22
tags:
- jquery
- js
categories:
- 前端
---

### code
![code](http://oj171eydn.bkt.clouddn.com/chengxutu4.jpg)

然后我们在html引入如图这个js,  
```bash
<script type="text/javascript">
    $(function() {   
        $("#aa").typewriter();    //测试插件
    }
</script>
<body>  
    <div id="aa">我们<h1>可以看到</h1>字显示<h2>出来</h2>就像输入一样</div>
</body>
大致效果:
![show](http://oj171eydn.bkt.clouddn.com/show1.jpg)
