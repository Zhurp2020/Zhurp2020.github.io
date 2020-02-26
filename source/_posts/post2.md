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
### 定位并操作元素
&emsp;&emsp;接下来，我们要做的是点击登录按钮。首先，我们要在页面上定位这个按钮。selenium提供了数种方法定位元素。例如`webdriver.find_element_by_class_name(name)`将返回匹配`class`是`name`的元素。此外，还可以通过`tag_name`、`id`、`css_selector`、`link_text`、`name`、`partial_link_text`、`xpath`等匹配元素。`webdriver.find_element_by_class_name(name)`将返回第一个匹配的元素。相应地，`webdriver.find_elements_by_class_name(name)`则会返回一个由所有找到的元素组成的`list`  
&emsp;&emsp;按下`F12`或鼠标右键检查可以查看网页的源代码。点击代码中的元素，我们可以看见相应的蓝框。一步步缩小范围，最终可以找到相应的代码。
![登录按钮的代码](/pics/pic2/5.jpg)
```html
<input type="button" value="登录" class="loginSub" onclick="goPassport2Login();">
```
&emsp;&emsp;那么，就可以写出定位该元素的代码
```python
LoginButton = driver.find_element_by_class_name('loginSub') 
```
&emsp;&emsp;通过`webelement.click()`方法可以点击该元素。
```python
LoginButton.click()
```
&emsp;&emsp;接下来，就跳转到了登录页面。在这个页面，需要定位三个元素：用户名和密码的输入框以及登录按钮。
![登录页面](/pics/pic2/6.jpg)
```html
<input type="text" name="username" id="username" placeholder="请输入账号/Campus ID Number">
<input type="password" name="password" id="password" placeholder="请输入密码/Password">
<input type="submit" name="login_submit" id="login-submit" value="登录/Login">
```
### 登录
&emsp;&emsp;写出定位这三个元素的代码
```python
UsernameInput = WebDriver.find_element_by_name('username')
PasswordInput = WebDriver.find_element_by_name('password')
LoginSubmit = WebDriver.find_element_by_name('login_submit')
```
&emsp;&emsp;这里我们需要进行五个操作：分别点击两个输入框并输入用户名和密码，点击登录按钮。可以用到Action Chain（动作链）。先通过`webdriver.AnctionChains(driver)`方法创建一个动作链：
```python
InputAction = webdriver.ActionChains(driver)
```
&emsp;&emsp;然后是点击和输入的操作。`.send_keys_to_element(element,keys_to_send)`用来模拟键盘输入。
```python
username = '' #你的用户名
password = '' #你的密码

InputAction.click(UsernameInput)
InputAction.send_keys_to_element(UsernameInput,username)
InputAction.click(PasswordInput)
InputAction.send_keys_to_element(PasswordInput,password)
InputAction.click(LoginSubmit)
```
&emsp;&emsp;最后，执行这个动作链。
```python
InputAction.perform()
```
&emsp;&emsp;可以把登录封装成一个函数。
```python
def login(username,password,WebDriver) :
    ''' 
    登录，参数:学校，用户名，密码，webdriver
    '''
    WebDriver.get("http://www.elearning.shu.edu.cn/portal")
    # 定位登录按钮并点击
    LoginButton = WebDriver.find_element_by_css_selector('.loginSub') 
    LoginButton.click()
    # 用户名密码输入框，提交按钮
    UsernameInput = WebDriver.find_element_by_name('username')
    PasswordInput = WebDriver.find_element_by_name('password')
    LoginSubmit = WebDriver.find_element_by_name('login_submit')
    # 输入用户名密码，提交       
    InputAction = webdriver.ActionChains(WebDriver)
    InputAction.click(UsernameInput)
    InputAction.send_keys_to_element(UsernameInput,username)
    InputAction.click(PasswordInput)
    InputAction.send_keys_to_element(PasswordInput,password)
    InputAction.click(LoginSubmit)
    InputAction.perform()
```