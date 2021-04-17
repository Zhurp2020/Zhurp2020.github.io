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
![git官网](/pics/pic0/1.jpg)  
&emsp;&emsp;这里主要用到Git来部署网站到Github Pages。关于Git的其他用法，同样将在另一篇文章中说明
1. Node.js  
&emsp;&emsp;访问[这里](https://nodejs.org/en/)下载安装Node.js  
![Node.js官网](/pics/pic0/2.jpg)  
&emsp;&emsp;至此，完成了所需工具的安装
## 建站
建站的流程可分为以下几步：
+ 配置工具
+ 注册登录Github账号，开通Github Pages
+ 建立博客
1. 配置工具
   1. 安装Hexo  
      &emsp;&emsp;打开Node.js Command Prompt（Node.js命令行），输入如下命令
      ``` bash
      $ npm install -g hexo-cli
      ```
      &emsp;&emsp;npm是Node.js的包管理工具。可以用来从npm服务器上下载安装第三方包，也可以将自己的包上传到服务器上。  
      &emsp;&emsp;Hexo是一款轻量级的博客框架，基于Node.js。写文章时使用Markdown语法，然后只需要简单的配置就可以渲染出静态网页文件并部署到Github Pages。
    1. VS Code插件安装  
      &emsp;&emsp;需要用到的是npm和vscode-hexo两个插件。进入扩展商店安装这两个插件。这样之后所有操作都可以在VS Code里面操作了。注意是图中的这两个插件。
      ![vscode-hexo插件](/pics/pic0/4.jpg)
      ![npm插件](/pics/pic0/5.jpg)
2. 注册登录Github账号，开通Github Pages   
   &emsp;&emsp;可以参考Github Pages网站上的帮助[这里](https://pages.github.com/)  
   ![Github Pages](/pics/pic0/6.jpg)  
   &emsp;&emsp;登录Github账号，新建一个仓库(repository)，命名一定要是`用户名.github.io`的格式，一定要一字不差。复制仓库地址备用。仓库地址看起来是这样的:`https://github.com/用户名/用户名.github.io.git`，当然你也可以通过配置SSH Key的方式来向仓库中上传文件。网站的部署将会通过push这个仓库完成。
   ![新建仓库](/pics/pic0/7.jpg)
3. 建立博客  
   1. 建站  
   &emsp;&emsp;打开VS Code，新建一个空文件夹，按下Ctrl+Shift+P打开命令面板，执行如下命令：
   ``` bash
   $ hexo init
   ```
   ![建站完成](/pics/pic0/8.jpg)
   &emsp;&emsp;之后我们需要在本地安装相应的插件。执行如下命令：
   ``` bash
   $ npm install saved packages
   ```
   &emsp;&emsp;执行完毕后会多出一个`node_modules`文件夹。  
   ![安装插件](/pics/pic0/9.jpg)  
   2. 写作  
   &emsp;&emsp;执行如下命令
   ``` bash
   $ hexo new
   ```
   &emsp;&emsp;layout可以不用填，title必填。如果title中有多个空格需要加上双引号。之后会在`source/_posts`文件夹下生成一个`title.md`的文件，打开就可以开始使用Markdown语法写作了。
   ![建立新页面](/pics/pic0/10.jpg)  
   3. 预览  
   &emsp;&emsp;在本地预览需要安装一个hexo-server插件。执行如下命令：
   ``` bash
   $ npm install and save dependency
   ```
   &emsp;&emsp;然后输入hexo-server，等待完成。
   ![安装插件](/pics/pic0/11.jpg)
   &emsp;&emsp;要开始预览，执行如下命令：
   ``` bash
   $ hexo server
   ```
   &emsp;&emsp;处理完成后，就可以在本地[4000端口](http://localhost:4000/)预览效果。会自动追踪文件变更然后实时更新效果，不必重启服务器。
  ![开启预览](/pics/pic0/12.jpg)
  ![预览效果](/pics/pic0/13.jpg)
## 部署
&emsp;&emsp;这里将使用git的方式部署博客。其他方式详见官方文档。打开博客文件夹下的`_config.yml`文件，在文件末尾添加如下代码，注意缩进：

``` yml
deploy: 
  type: git  
  repo: 'https://github.com/用户名/用户名.github.io.git' 
  branch: master
```
&emsp;&emsp;然后执行如下命令：
``` bash
$ hexo deploy
```
&emsp;&emsp;这一步会渲染相应的静态网页文件，存放在`public`文件夹下，之后会将仓库`master`分支下的所有文件覆盖。过几分钟后，访问`用户名.github.io.`就可以看到效果了。
## 更多
+ 多台电脑编辑博客
+ 博客进一步美化：
  + 安装主题
  + 魔改主题 
