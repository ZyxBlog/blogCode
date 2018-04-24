---
title: js制作tab标签
date: 2016-09-20 08:44:26
tags:
- js
- css
categories:
- 前端
---

### 实现简单tab标签
#### 第一步还是配置静态html文件
```bash
<div id="whole">
    <div class="tabname">
        <ul>
            <li><a href="#">成电新闻</a></li>     
            <li><a href="#">学院概况</a></li>
            <li><a href="#">院系部门</a></li>
            <li><a href="#">合作交流</a></li>
        </ul>
    </div>
    <div id="tab">
        <p>朝气蓬勃的青年大学生是实现中华民族伟大复兴的希望，是实现第二个百年目标的主要力量。随着中国经济和综合国力的增长，在建设世界一流大学的过程中，大学要从战略高度出发，在办学实践中自觉加强“四个自信”教育引领，不仅要培养有创新精神、有全球视野、有国际竞争力的领军型人才，更要培养具有历史使命感和时代责任感的合格建设者和可靠接班人。</p>
        <p style="display:none;">在当前纷繁复杂的信息时代，传统的徒劳说教无益，这就要求大学一方面不断提高思想政治教育课程的针对性、吸引力和时效性，大力提升思想政治教育水平，另一方面要加强人文通识教育，注重文理结合、科学与人文融合，夯实精英人才培养的通识教育基础。</p>
        <p style="display:none;">未来国与国之间的竞争，核心是具有创新能力的青年人才的竞争。随着中国经济的快速增长，青年人参与国际交流的机会越来越多。国际交流带来了开阔的眼界和拓展的思维，也带来了不同文化的交流和碰撞。只有对中国道路、中国文化的坚定自信，才能使我们的年轻学子在文化交流中站得住、站得稳。</p>
        <p style="display:none;">中华民族的伟大复兴之路任重道远，大学的根本使命在于立德树人。建设中国特色世界一流大学的过程，是培养德智体美全面发展，对脚下这片土地、对诞生养育我们的中华民族有深厚感情的青年社会主义建设者和接班人的过程</p>
    </div>
</div>
```

#### 接下来是css样式
```bash
<style type="text/css">
* {
    padding: 0;
    margin: 0;
}   
li {   
    list-style: none;
    float: left;
}
a {  
    text-decoration: none;
    display: block;
}
#whole {
    width: 750px;
    height: 450px;
    margin: 0 auto;
    border: 1px solid rgb(92, 101, 92);
}   
.tabname {
    width: 100%;
    height:50px;
    border-bottom: 3px solid #2e0fec;
}
#whole .tabname ul {
    width: 600px;
    height: 30px;
    padding-top: 20px;
    margin-left: 45px;
}
#whole .tabname ul li{   
    width: 100px;
    height: 30px;
    line-height: 30px;
}
#whole .tabname ul li a{   
    padding-left: 18px;
    color: #2e0fec;
    font-weight:bold;
}
#tab {
    margin:15px 45px;
}
#tab p {
    color: #808080;
}
</style>
```

#### js文件
```bash
<script>
window.onload = function() {  
    var whole = document.getElementById("whole");
    var tagli = whole.getElementsByTagName("li");
    var tab = document.getElementById("tab");
    var tabdiv = tab.getElementsByTagName("p");
    for (i = 0; i < tagli.length; i++) {   //执行函数
      switchTab(i);
    }   
    //tab切换
    function switchTab(i)    //函数分离
        tagli[i].onmouseover = function() {   //样式改变
            this.style.backgroundColor = "#2e0fec";
            this.getElementsByTagName("a")[0].style.color = "#FFFFFF";    
            for (j = 0; j < tabdiv.length; j++) {
                if (i == j) {       
                    tabdiv[j].style.display = "block";
                } else {      
                    tabdiv[j].style.display = "none";
                }
            }  
        }
        tagli[i].onmouseout = function() {      
            this.style.backgroundColor = "#FFFFFF";     
            this.getElementsByTagName("a")[0].style.color = "#2e0fec";
        }
    }
}
</script>
```
主要还是传递参数,然后循环出tab标签,实现比较基础,简单,如果用jquery写的话,可以少写一些循环,实现功能更快一些.
