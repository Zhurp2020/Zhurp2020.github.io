---
title: 如何优雅地刷学习通课程
date: 2020-02-22 14:00:34
tags:
  - python
  - github
categories: Tech
summary: 基于python和Selenium的学习通刷课脚本
---
# 如何优雅地刷学习通课程
项目Github地址：[这里](https://github.com/Zhurp2020/AutoStudy)
克隆这个仓库：
``` bash
$ git clone https://github.com/Zhurp2020/AutoStudy.git
```
## 工具安装
+ python
+ 一个编辑器，推荐使用VS Code
+ （非常推荐）分布式版本控制工具Git
+ Selenium库
+ Chorme Webdriver
1. python   
   &emsp;&emsp;在官网[这里](https://www.python.org/)下载Python并安装
   ![python官网](/pics/pic2/1.jpg)
2. VS Code  
   &emsp;&emsp;访问[这里](https://code.visualstudio.com/)下载安装VS Code。然后在扩展商店里安装python扩展。  
   ![VS Code官网](/pics/pic0/0.jpg) 
   ![python扩展](/pics/pic2/2.jpg) 
3. Git   
   &emsp;&emsp;访问[这里](https://git-scm.com/)下载安装git，然后完成相关配置。  
![git官网](/pics/Pic0/1.jpg)
4. Selenium库  
   &emsp;&emsp;可以使用`pip`安装这个库
   ``` bash
   pip install selenium
   ```
   &emsp;&emsp;这是一个自动化测试库，他可以自动操作浏览器。比如：访问页面，定位元素，输入点击等等。
5. Chorme Webdriver  
   &emsp;&emsp;访问[这里](https://chromedriver.chromium.org/downloads)下载chorme Webdriver，注意**一定要和当前使用的chorme版本相对应！**
   ![chorme Webdriver](/pics/pic2/3.jpg)
   &emsp;&emsp;下载完成后，把他解压，然后把`chormedriver.exe`移到python的安装目录下，这个目录看起来可能是这样的：`C:\Users\Administrator\AppData\Local\Programs\Python\Python38`
## 代码
selenium的官方文档在[这里](https://www.selenium.dev/documentation/zh-cn/getting_started/)  
找一个文件夹，新建一个`.py`文件，然后开始撸代码吧！  
先导入模块  
```python
import selenium
```
### 第一步
&emsp;&emsp;首先启动一个浏览器。当然除了chorme，selenium库还支持firefox等其他主流浏览器。这里用chorme作为例子。新建一个webdriver对象：
```python
driver = webdriver.Chrome() 
```
&emsp;&emsp;通过`webdriver.get(url)`方法访问一个页面。注意这个方法不会新建一个标签页，而是直接在当前页面上跳转。
```python
driver.get('http://www.elearning.shu.edu.cn/portal')
```
&emsp;&emsp;可以运行测试一下效果
![](/pics/pic2/4.jpg)