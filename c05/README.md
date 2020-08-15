# 第五章 代码重用与函数重写
## 5.1 代码重用的好处
### 5.1.1 成本
### 5.1.2 可靠性
### 5.1.3 一致性
## 5.2 使用require()和include()函数
* require()函数  
语句执行失败后，给出一个 致命的错误  
* include()函数  
语句执行失败后，给出一个 警告
* require_once  
确保一个被引入的文件只能被引入一次 运行速度较快
* include_once  
确保一个被引入的文件只能被引入一次 运行速度较快

### 5.2.1 使用require()函数引入代码
* reusable.php
```
<?php
echo 'echo 'Here is a very simple PHP statement.<br />';
?>
```
* main.php
```
<?php
echo 'This is the main file.<br />';
require('reusable.php');
echo 'The script will end now.<br />';
?>
```
### 5.2.2 使用require()制作Web站点模版
* 测试一 建站  
[home.html](../home.html)  
[style.css](../style.css)
* 测试二 模块化  
[home.php](../home.php)  
[header.php](../header.php)  
[footer.php](../footer.php)  
* 测试三 框架  
[framework.php](../framework.php)  
[header.php](../header.php)  
[footer.php](../footer.php)  

### 5.2.3 使用auto_prepend_file和auto_append_file

## 5.3 使用PHP函数
### 5.3.1 调用函数
### 5.3.2 调用未定义函数
* 在函数调用中,错误地拼写函数名称  
* 调用一个没有在当前版本声明的函数将导致错误  
* 所调用的函数为PHP扩展库函数，
### 5.3.3 理解大小写和函数名称
* 函数调用 不 区分大小写
## 5.4 自定义函数
* 函数的声明和调用  
[basic_fuc.php](../basic_func.php)
## 5.5 了解函数基本结构
函数命名  
* 不能和已有函数重名  
* 只能包含字母、数字和下划线  
* 不能以数字开始  

变量函数  
$name();  

## 5.6 参数使用

## 5.7 理解作用域

## 5.8 引用传递和值传递

## 5.9 使用return关键字

## 5.10 递归实现

## 5.11 进一步学习

## 5.12 下一章
