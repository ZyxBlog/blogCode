---
title: webpack打包速度的issue
date: 2017-08-07 13:00:22
tags:
- webpack
categories:
- 前端
---
最近一直在做快站的投票活动，项目接近尾声，在build投入生产环境上线的时候，却发现一个比较费时的事，webpack打包时间太长接近1分钟。
一两次还好，上线到预发次数多了，觉得很浪费时间。
这个问题的原因觉得很明显：该项目安装包很多，即使没有经常变动的安装包，在投入生产环境中仍就每一次都重新打包。
![show](http://oj171eydn.bkt.clouddn.com/package.png)
解决方法：既然是包的数目影响了webpack打包所有包的速度，我感觉webpack应该会有相应的插件去解决这个问题，或者应该有相关的配置去优化速度。
来重新对webpack文档进行细细查看之下，发现确实有这么个玩意能够解决这个问题，有DllPlugin和DllReferencePlugin这两个插件配合使用来解决这个问题。
具体是DllPlugin的作用是把需要打包的第三方库，打包成一个js和一个json，json文件记录这每个打包的模块地址和id，而与之相配合的DllReferencePlugin插件主要是通过读取json文件来使用打包的模块。

首先在webpack配置的文件夹中新建一个webpack.dll.conf.js
```bash
var path = require('path');
var webpack = require('webpack');
module.exports = {    
    entry: {      
        vender: ['vue', 'vue-router', ...]          // 非异步加载的插件名称    
    },    
    output: {        
        path: path.join(__dirname, '../vote/js'),        
        filename: '[name].dll.js',        
        library: '[name]_library'    },    
        plugins: [        
            new webpack.DllPlugin({            
                path: path.join(__dirname, '.', '[name]-manifest.json'),            
                name: '[name]_library'        
            }),        
            new webpack.optimize.UglifyJsPlugin({            
                compress: {                
                    warnings: false            
                }        
            })    
        ]
    }
}
```
然后在package.json中配置命令，在scripts中加上’build:dll’: “webpack –config build/webpack.dll.conf.js”。继而使用npm run build:dll 命令来生成vender.dll.js和vender-manifest.json
接着在index.html中引入vender.dll.js
最后一步是在devServer.js中通过DllReferencePlugin来是使用DllPlugin生成的文件。
```bash
...
plugins: [    
    new webpack.DllReferencePlugin({        
        context: path.resolve(__dirname, '..'),        
        manifest: require('./vender-manifest.json')    
    })
]
...
```
使用之后的webpack打包速度是20s左右，节约了将近2/3的时间
PS： 在解决问题之后搜索了一下关于这两个插件的具体情况，以便防止有啥坑，果然发现不能将所有的第三包打包进去，否则包太多会影响首屏加载的时间，异步加载的包就没有必要打包进来。
