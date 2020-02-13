---
title: Vscode、github、hexo：如何搭建自己的博客
date: 2020-02-02 17:40:02
tags: 
  - Vscode 
  - github
  - hexo
summary: 你好，欢迎来到这里。
categories: Tech
author: Zhurp
---
# Vscode、github、hexo：如何搭建自己的博客
你好，欢迎来到这里。以后这里也许会更新，也许不会。  
这篇是一个教程，完全从零开始搭建一个博客。
也可以参考hexo的官方文档[这里](https://hexo.io/zh-cn/docs/)。
## 工具安装
这些是需要安装的工具。推荐在官网下载他们。  
+ Visual Studio Code，一个由微软开发的编辑器
+ Git，分布式版本控制工具
+ node.js，一个js运行环境
1. VS Code   
&emsp;&emsp;访问[这里](https://code.visualstudio.com/)下载安装VS Code。
![VS Code官网](/pics/pic0/0.jpg)    
&emsp;&emsp;这款编辑器支持html,css,js,markdown等文件的编辑，还有用户和官方写的各种插件，靠这些插件，可以靠这一个软件就完成博客建立编辑部署的全过程。   
&emsp;&emsp;它还有很多优点，比如内嵌了git的支持，快捷键很方便等等等等。  
&emsp;&emsp;关于这款编辑器的更多用法，将在另一篇文章中详细说明。
2. Git  
&emsp;&emsp;访问[这里](https://git-scm.com/)下载安装git，然后完成相关配置。  
![git官网](/pics/pPic0/1.jpg)  
&emsp;&emsp;这里主要用到Git来部署网站到Github Pages。关于Git的其他用法，同样将在另一篇文章中说明
1. Node.js  
&emsp;&emsp;访问[这里](https://nodejs.org/en/)下载安装Node.js  
![Node.js官网](/pics/pic0/2.jpg)  
&emsp;&emsp;至此，完成了所需工具的安装
## 建站
建站的流程可分G为以下几步：
+ 配置工具
+ 注册登录Github账号，开通Github Pages
+ 建立博客
1. 配置工具
   1. 安装Hexo  
      &emsp;&emsp;打开Node.js Command Prompt（Node.js命令行），输入如下命令
      ```n4js
      $ npm install -g hexo-cli
      ```
      &emsp;&emsp;npm是Node.js的包管理工具，用来安装。可以用来从npm服务器上下载第三方包，也可以将自己的包上传到服务器上。  
      &emsp;&emsp;Hexo是一款轻量级的博客框架，基于Node.js。写文章时使用Markdown语法，然后只需要简单的配置就可以渲染出静态网页文件并部署到Github Pages。
    2. VS Code插件安装  
      &emsp;&emsp;需要用到的是npm和vscode-hexo两个插件。进入扩展商店安装这两个插件。这样之后所有操作都可以在VS Code里面操作了。
      ![vscode-hexo插件](/pics/pic0/4.jpg)
      ![npm插件](/pics/pic0/5.jpg)
      &emsp;&emsp;注意是图中的这两个插件
2. 注册登录Github账号，开通Github Pages
   &emsp;&emsp;可以参考Github Pages网站上的帮助[这里](https://pages.github.com/)
   ![Github Pages](/pics/pic0/6.jpg)
   &emsp;&emsp;登录Github账号，新建一个仓库，命名一定要是`用户名.github.io`的格式，一定要一字不差。
## 部署
## 更多
