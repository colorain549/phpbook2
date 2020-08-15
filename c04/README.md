# 第四章 字符串操作与正则表达式
## 4.1 创建一个示例应用: 智能表单邮件
函数 isset()  
* isset()可用于检查用户是否已经填写了所有必填的表单域  
* <font color="red">函数 mail()待测试</font>  
* mail($toaddress, $subject, $mailcontent, $fromaddress);
1. $toaddress(必填，收件地址)
2. $subject(必填，主题行)
3. $mailcontent(必填，信息内容)
4. $fromaddress(可选，有效的邮件header，详情请查看RFC822文档)  

index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bob's Auto Parts - Customer Feedback</title>
</head>
<body>
    <h1>Customer Feedback</h1>
    <p>Please tells us what you think</p>
    <form action="processfeedback.php" method="post">
        <label for="">Your name: </label><br />
        <input type="text" name="name"><br />
        <br />
        <label for="">Your email address: </label><br />
        <input type="text" name="email"><br />
        <br />
        <label for="">Your feedback: </label><br />
        <textarea name="feedback" id="" cols="18" rows="3"></textarea><br />
        <input type="submit" value="Submit"">
    </form>
</body>
</html>
```
processfeedback.php
```
<?php
$name = $_POST['name'];
$email = $_POST['email'];
$feedback = $_POST['feedback'];
//
$toaddress = "colorain@live.com";

$subject = "Feedback from web Site";

$mailcontent = "name: " . filter_var($name) . "<br /> . "email: " . $email . "<br />" . "comments: " . $feedback . "<br />";

mail($toaddress, $subject, $mailcontent);
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bob's Auto Parts - Feedback Submitted</title>
</head>
<body>

    <h1>Feedback submitted</h1>
    <p>Your feedback has been sent.</p>
</body>
</html>
```
## 4.2 字符串的格式化
### 4.2.1 字符串截断: chop()、ltrim()和trim()
| 函数 | 说明 |
| ---- | ---- |
| trim()| 除去字符串前后的空格 |
| ltrim()| 除去字符串前的空格 |
| rtrim()| 除去字符串后的空格 |
| chop() | rtrip()的别名函数 |
```
$name = $_POST['name'];
$email = $_POST['email'];
$feedback = $_POST['feedback'];
```
### 4.2.2 格式化字符串以便输出
1. 格式化字符串以便输出
2. 使用htmlspeialchars()函数过滤输出至浏览器的字符串
* 将在HTML中有特殊含义的字符转换为等价的HTML实体
3. 为其他输出形式过滤字符串  
* str_replace()函数
* 用特定字符串替换一个完整字符串
* 解决header注入问题
4. 使用HTML格式化:nl2br()函数
* 将字符串作为输入参数，用HTML中的br标记代替字符串中的换行符)
5. 为打印输出字符串而格式化字符串

* echo 将字符串输出到浏览器
* printf() 具有返回值1 将一个格式化的字符串输出到浏览器中 可使用<font color=red>转换规范</font>
* sprintf() 具有返回值1 返回一个格式化后的字符串
6. 改变字符串中的大小字母
* strtoipper() 全大写
* strtolower() 全小写
* ucfirst() 句首字母大写
* ucwords() 词首字母打斜

htmlspecial()函数支持的特殊字符及其对应的HTML实体
|  字符 | 翻译  |  字符 | 翻译  |
|  --  | ----  |  --  | ----  |
|   &  | &amp  |   <  | &lt   |
|   "  | $quot |   >  | &gt   |
|   '  | $apos |      |       |

参数  
1. flags，可选，指定如何完成翻译；
2. encoding，可选，指定转换的编码方式，默认编码是UTF-8；
3. double_encode，可选，指定了是否对HTML实体进行编码。

htmlspecialchars()函数flags参数的可能值
| 标志 | 意义 |
|  -  |  -  |
| ENT_COMPAT | 对双引号编码，不对单引号进行编码 |
| ENT_NOQUOTES | 不对单引号或双引号 |
| ENT_QUOTES | 对单引号和双引号进行编码 |
| ENT_HTML401 | 将代码当作HTML4.01 |
| ENT_XML1 | 将代码当作XML1 |
| ENT_XHTML | 将代码XHTML |
| ENT_HTML5 | 将代码HTML5 |
| ENT_IGNORE | 不返回空字符串，并且忽略无效的代码单元序列。不推荐。 |
| ENT_SUBSTITUE | 用Unicode替换字符替换无效的代码单元序列 |
| ENT_DISALLOWED | 用Unicode替换字符替换无效的代码点 |

转换规范  
格式: 
| 类型 | 意义 |
|  -  |  -  |
| % | 文本字符 |
| b | 解释为整数并作为二进制输出 |
| c | 解释为整数并作为字符输出 |
| d | 解释为整数并作为小数输出 |
| e | 解释为双精度并且以科学技术法打印，精度是小数点后面的数字个数 |
| E | 与e相同，但将打印大写E |
| f | 解释为双精度并作为浮点数输出 |
| F | 解释为浮点并打印与locale无关的浮点数 |
| g | 转换规范类型e或f的简短输出 |
| G | 转换规范类型E或F的简短输出 |
| o | 解释为整数并作为八进制输出 |
| s | 解释为字符串并作为字符串输出 |
| u | 解释为整数并作为非指定小数输出 |
| x | 解释为整数并作为带有小写字母a-f的十六进制数输出 |
| X | 解释为整数并作为带有大写字母A-F的十六进制数输出 |

## 4.3 使用字符串函数连接和分割字符串
### 4.3.1 使用函数explode()、implode()和join()
* explode()函数  
> 函数原型:   
array explode(string seperator, string input[, int limit])  

字符串大小写混合的无法使用，可使用strtoupper()或strtolower()转换后再使用
```
// 将email分割成两部分
$email = "123456@789.com";
$email_array = explode('@', $email);
echo $email_array[0] . "<br />";
echo $email_array[1];
```
* implode()函数和join()函数的作用是相同的，与explode()相反   
从数组中取出元素，用传入第一个参数的字符将它们连接在一起。
```
$email = "123456@789.com";
$email_array = explode('@', $email);
$new_char = implode('a', $email_array);
echo $new_char;
```
### <font color=red> 4.3.2 使用strtok()函数</font>
### 4.3.3 使用substr()函数
函数 substr() 允许我们访问一个字符串给定起点和终点的子字符串。
  
> 函数原型  
string substr(string string, int start[, int length]);  

示例
```
$test = 'Your customer service is excellent';
substr($test, 1);       // 返回"our customer service is excellent"
substr($test, -9);      // 返回"excellent"
substr($test, 0, 4);    // 返回"Your"
substr($test, 5, -13);  // 返回"customer service"
```
## 4.4 字符串比较
### 4.4.1 字符串的排序: strcmp()、strcasecmp()和strnatcmp()
* strcmp(string str1, string str2)  
若相等，返回0;  
按字典顺序，str1 > str2，返回一个正数，否则返回一个负数;
区分大小写。
* strcasecmp() 不区分大小写
* strnatcmp() 按自然排序

[自然排序](http://www.naturalordersort.org/)
### 4.4.2 使用strlen()函数判断字符串的长度
```
//例1
echo strlen("hello");   // 返回5 
```
```
//例2
if (strlen($email) < 6){
    echo 'That email address is not valid';
    exit;
}
```
## 4.5 使用字符串函数匹配和替换子字符串
### 4.5.1 在字符串中查找字符串: strstr()、strchr()、strrchr()和stristr()
* strstr()函数   
> 函数原型:  
string strstr(string haystack, string needle[, bool before_needle=false]);  

在一个较长的字符串中查找需要匹配的字符串或字符
* strchr()函数  
在一个较长的字符串中查找需要匹配的字符串或字符
* strrchr()函数  
不区分大小写。
* stristr()函数  
从最后出现needle的位置开始往前返回被搜索字符串
### 4.5.2 查找子字符串的位置: strpos()和strrpos()
建议使用strpos()函数替代strstr()函数来查看一个子字符串在一个字符串中出现的位置，因为strpos()运行速度快
* strpos()
> 函数原型:  
int strpos(string haystack, string needle[, int offset=0]);
```
// 例
$test = "Hello world";
// 显示数值 4
echo strpos($test, "o")
// Offset参数，可选，指定被搜索字符串的可事实上位置
echo strpos($test, "o", 5)
```
* strrpos()函数  
1. 返回被搜索字符串在haystack中最后一次出现needle的位置  
2. 可使用运算符"==="测试返回值  
```
// 例
$test = "Hello world";
$result = strpos($test, "H");
if ($result === false){
    echo "Not found";
} else {
    echo "Found at position: " . $result;
}
```
### 4.5.3 替换子字符串: str_replace()和substr_replace()
* str_replace()  
查找替换特定的字符串   
> 函数原型:  
mixed str_replace(mixed needle, mixed new_needle, mixed haystack[, int &count]);  
```
// 例
$offcolor = ['color', 'blue'];
$feedback = 'blue is my favorite color';
$feedback = str_replace($offcolor, '???', $feedback);
echo $feedback;
```
* substr_replace()  
在给定的位置中查找并替换字符串中特定的子字符串  
> 函数原型: TODO
```
$test = "Hello world";
$test = substr_replace($test, '???', 6);
echo $test . "<br />";
$test = "Hello world";
$test = substr_replace($test, '???', 6, 3);
echo $test . "<br />";
```
## 4.6 正则表达式的介绍
### 4.6.1 基础知识
* 可精确匹配字符
* 可用特殊字符来指定表达式的元意义(meta-meaning)
### 4.6.2 分隔符
分隔符'/'  
```
// 匹配"shop"的正则表达式
/shop/
```
```
// 在这种表达式中匹配字符"/"，需要用"\"来转义
/http:\/\//
```
```
// 分隔符'#'
#http://#
```
在结束分隔符后添加 模式修饰符i(不区分大小写匹配)
```
/shop/i
```
### 4.6.3 字符类和类型
字符“.”作为匹配除换行符(\n)之外任何字符的通配符
```
// 匹配 诸如“cat”、"mat"和"#at"的字符
/.at/
```
使用方括号([])指明要匹配的字符类型
```
// 列出字符集合
/[aeiou]/
```
使用连字符 " - " 描述一个范围
```
// 限定第一个字母是a到z之间的字符
/[a-z]at/
```
```
/[a-z][A-Z]/
```
```
// ^用在[]内 不属于某个集合
/[^a-z]/
```
用于PCRE风格正则表达式的字符类
| 类 | 匹配 | 类 | 匹配 |
| -- | -- | -- | -- |
| [[:album:]] | 文本数字字符 | [[:punct:]] | 标点符号 |
| [[:alpha:]] | 字母字符 | [[:blank:]] | 制表符和空格 |
| [[:asci:]] | ASCII字符 | [[:lower:]] | 小写字母 |
| [[:space:]] | 空白字符 | [[:upper:]] | 大写字母 |
| [[:cntrl:]] | 控制符 | [[:digit:]] | 小数 |
| [[:print:]] | 所有可打印字符 | [[:xdigit:]] | 十六进制数字 |
| [[:graph:]] | 除空格外所有可打印的字符 | [[:word::]] | “word”字符(字母、数字或下划线) |
```
// 包含字母字符或1到5数字的字符串
/[:alpha]1-5/
```
### 4.6.4 重复
符号" * "表示这个模式可重复出现 0次 或多次  
符号" + "表示这个模式可重复出现 1次 或多次  
符号" ? "表示这个模式可出现 1次 或0次
```
// 至少有一个字母字符
/[[:alnum:]]+/
```
### 4.6.5 子表达式
使用 圆括号() 实现 表示“至少这些字符串中的一个需要匹配该模式”
```
// 匹配"large"、"very largr"、"very very large"等
/(very)*large/
```
### 4.6.6 子表达式计数
在 花括号{} 中使用数字表达式 指定内容允许重复的次数
```
/(very ){3}/
```
```
/(very ){2, 4}/
```
```
/(very ){2,}/
```
### 4.6.7 定位到字符串的开始或末尾
脱字符号 ^ 用于 正则表达式的 开始
```
// 字符串开始处匹配bob
/^bob/
``` 
字符 $ 用于 正则表达式的末尾
```
// 以com为结束的字符串
```
```
// 匹配只包含 a 到 z 之间的一个字符串
/^[a-z]$/
```
### 4.6.8 分支
正则表达式使用“|”来表示模式选择
```
// 匹配com、edu或net
/com|edu|net/
```
### 4.6.9 匹配特殊字符
|特殊字符|写法|
|------|------|
| . | \\. |
| $ | \\$ |
| \ | \\\\ |
### 4.6.10 元字符一览
方括号 外 的特殊字符
|字符|意义|字符|意义|
|---|---|---|---|
| \ | 转义字符 | ) | 子模式的结束 |
| ^ | 在字符串 开始 匹配 | * | 重复0次或多次 |
| $ | 在字符串 末尾 匹配 | + | 重复1次或多次 |
| . | 匹配除换行符(\n)之外的字符 | { | 最小/最大量记号的开始 |
| \|| 选择分支的开始(读为或) | } | 最小/最大量记号的结束 |
| (|子模式的开始 | ? | 标记一个子模式是可选的 |
方括号 内 的特殊字符
| 字符 | 意义 |
| --- | --- |
| \ | 转义字符 |
| ^ | 非，仅在开始位置使用 |
| - | 指定字符范围 |
### 4.6.11 转义序列  
转移序列是一种模式定义，它以反斜杠字符( \\ )为开始。  
1. 转义特殊字符(如 \\ /)
2. 用在代表非打印字符的字符前面（如\n、\r、\t、\e）
3. 正则表达式的特殊字符类型(如下表)

| 字符类型 | 含义 | 字符类型 | 含义 |
| ----- | ----- | ----- | ----- |
| \d | 十进制数字 | \S | 任意非空白字符 |
| \D  | 任意非十进制数字 | \v | 垂直空白字符 |
| \h | 水平空白字符 | \V | 任意非垂直空白字符 |
| \H | 任意非水平空白字符 | \w | 单词字符 |
| \s | 空白字符 | \W | 任意非单词字符 |
### <font color=red>4.6.12 回溯引用  </font>
### <font color=red>4.6.13 断言  </font>
### <font color=red>4.6.14 在智能表单中引用 </font> 
## <font color=red>4.7 用正则表达式 查找 子字符串  </font>
## <font color=red>4.8 用正则表达式 替换 子字符串</font>
## 4.9 使用正则表达式 分割 字符串
preg_split()  
> 函数原型:   
array preg_split(string pattern, string subject[, int limit=-1[, int flag=0]]);
<?php
$address = 'username@example.com';
$arr = preg_split('/\.|@/', $address);
while(list($key, $value) = each($arr)){
    echo '<br />'.$value;
}
?>
```
## <font color=red>4.10 进一步学习</font>
## <font color=red>4.11 下一章</font>