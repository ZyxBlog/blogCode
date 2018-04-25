---
title: js实现上传前与预览
date: 2016-12-14 12:42:35
tags:
- js
categories:
- 前端
---

### html部分
```bash
<form>   
    <input type="file" name="face" id="upload" value="正面" style="display:none;" />   
    <img id="face"  src="#" alt="图片在此显示" style="width:60px;height:60px;" />
</form>
```

### js
为了美观所以上面对input的file进行隐藏,然后我们写入js
```bash
function getObjectURL(file) {  
    var url = null ;  
    if (window.createObjectURL != undefined) {     // basic    
        url = window.createObjectURL(file);  
    } else if (window.URL != undefined) {     // mozilla(firefox)    
        url = window.URL.createObjectURL(file);  
    } else if (window.webkitURL != undefined) {      // webkit or chrome    
        url = window.webkitURL.createObjectURL(file);
    } else {    
        alert("该浏览器不能实现预览功能!");  
    }  
    return url;
}
```
这里主要是用getObjectURL获取的,然后兼容一下各个浏览器,除了IE8,然后我们调用一下.

### 图片上传
```bash
$("#face").click(function () {  
    $("#upload").click();      //隐藏了input:file样式后，点击头像就可以本地上传  
    $("#upload").on("change", function() {    
        var objUrl = getObjectURL(this.files[0]);  //获取图片的路径，该路径不是图片在本地的路径    
        if (objUrl) {      
            $("#face").attr("src", objUrl);          //将图片路径存入src中，显示出图片    
        }
    });
});
```

### show
![show](http://oj171eydn.bkt.clouddn.com/show10.png)

还有就是函数结合createRange,实现上传图片的预览,这里就暂不详述了.
