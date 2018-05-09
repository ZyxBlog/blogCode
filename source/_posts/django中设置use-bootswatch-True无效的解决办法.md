---
title: django中设置use_bootswatch=True无效的解决办法
date: 2018-03-01 13:57:26
tags:
- python
categories:
- 后台
---
首先，原因是python2.7django1.9xadmin采用源代码的方式引入到项目中在xadmin使用的过程中,设置“use_bootswatch=True”,企图调出主题菜单,显示更多主题。然而设置了后,发现主题还是默认和bootstrap2,深入跟踪源代码,发现/xadmin/plugins/themes.py下的block_top_navmenu方法,当use_bootswatch为True的时候,就会使用httplib2

解决方案：
1. 安装requests
```bash
pip install requests
```

2.在xadmin源码文件夹下的themes.py中引入requests

3.修改block_top_navmenu方法:
```bash
def block_top_navmenu(self, context, nodes):
      themes = [
          {'name': _(u"Default"), 'description': _(u"Default bootstrap theme"), 'css': self.default_theme},
          {'name': _(u"Bootstrap2"), 'description': _(u"Bootstrap 2.x theme"), 'css': self.bootstrap2_theme},
      ]
      select_css = context.get('site_theme', self.default_theme)
      if self.user_themes:
          themes.extend(self.user_themes)

      if self.use_bootswatch:
          ex_themes = cache.get(THEME_CACHE_KEY)
          if ex_themes:
              themes.extend(json.loads(ex_themes))
          else:
              ex_themes = []
              try:
                  flag = False
                  if flag:
                      h = httplib2.Http()
                      resp, content = h.request("http://bootswatch.com/api/3.json", 'GET', '',
                                                headers={"Accept": "application/json",
                                                         "User-Agent": self.request.META['HTTP_USER_AGENT']})
