# PHP 第一章 快速入门教程
## <font color=red> 1.1 开始之前: 了解PHP</font>
## <font color=red> 1.2 创建示例Web应用: Bob 汽车零部件商店</font>
### 1.2.1 创建订单表单
* 表单的 action 属性被设置为 PHP脚本名称  
* 一般地，action 属性值是用户点击提交按钮时将要载入的URL。  
* 用户在表单中输入的数据将按照 method 属性中指定的HTTP 方法发送到这个 URL
1. get 附加在URL的结尾   
2. post 以单独信息的形式发送
### 1.2.2 表单处理
* 在 form 标记的 action 属性中指定的处理脚本
## <font color=red> 1.3 在HTML中嵌入PHP </font>
### 1.3.1 PHP标记
XML风格
```
<?php
    // code
?>
```
### 1.3.2 PHP语句
* 分号(;)是用来分隔语句的
### 1.3.3 空格
* PHP 引擎会忽略空格字符  
1. 换行(回车)
2. 空格
3. Tab(制表符)
### 1.3.4 注释
C 语言风格
```
/*
    code
*/
```
Shell 语言风格
```
# code
```
## 1.4 添加动态内容
### 1.4.1 调用函数
date()函数的调用
```
date('H:i, jS F')
```
### 1.4.2 使用date()函数
* 如果date()函数给出未设置时区的警告，需在 php,ini文件中添加date.timezone设置。
## <font color=red>1.5 访问表单变量</font>
### 1.5.1 表单变量
获取提交的数据并赋值给变量
```
$varName = $_POST['name']
```
* htmlspecialchars()函数 过滤数据
### 1.5.2 字符串连接
* 点号(.) 是 字符串连接符
### 1.5.3 变量和字面量
* 变量 存储值或计算结果的容器(自己的理解)
* 字面量 它的值来自其字面值  
```
// pieces 是 字面量
echo '$count pieces'; 
```
## 1.6 理解标志符
* 标志服不能以数字开始  
* 不能创建一个与已有函数同名的函数
## <font color=red> 1.7 检查变量类型 </font>
### 1.7.1 PHP的数据类型
1. Integer(整数) 整数
2. Float(浮点数) 实数
3. String(字符串) 字符串
4. Boolean(布尔) true 或 false
5. Array(数组) 保存具有相同类型的多个数据项
6. Object(对象) 用来保存类的实例
### <font color=red> 1.7.2 类型强度 </font>
### 1.7.3 类型转换
```
// 在希望进行类型转换的 变量 之前的圆括号 中插入需要转换为的临时数据类型
$num = 0;
$num = float($num)
```
### 1.7.4 可变变量
```
// 一个变量的值 作为 另一个变量的名称
$firstVar = 'fisrtValue';
$$firstVar = "secondValue";
// 上面两行代码 等价于
$firstValue = "secondValue"
```
* 可使用可变变量和for循环语句来遍历多个表单域
* 通过动态地创建变量名称，可依次访问每个表单域
```
// 若有名为 name1、name2、name3等的表单域
for ($i=0; $i<=$numnames; $i++){
    $temp = "name$i";
    echo htmlspecialchars($$temp).'<br />';
}
```
## 1.8 声明和使用常量
define函数 定义常量
```
define('TIREPRICE', 100);
define('OILPRICE', 10);
define('SPARKPRICE', 4);
echo TIREPRICE; // 返回100
```
phpinfo()函数  
给出一个PHP预定义常量和变量的列表，以及其他有用的信息
## <font color=red> 1.9 理解变量作用域？？？ </font>
关于作用域，PHP定义的6条规则  
* 1  
* 2 
* 3
* 4
* 5 
* 6  

超级全局变量 的完整列表
* $GLOBALS()
* $_SERVER()
* $_GET()
* $_POST()
* $_COOKIE()
* $_FILES()
* $_ENV()
* $_REQUEST()
* $_SESSION()

## <font color=red>1.10 使用操作符</font>
### 1.10.1 算术操作符 
| 操作符 | 名称 |
| --- | ---|
| + | 加 |
| - | 减 |
| * | 乘 |
| / | 除 |
| % | 取余 |
### 1.10.2 字符串操作符
* 字符串连接符(.)
### 1.10.3 赋值操作符
#### 1.10.3.1 赋值运算返回值
* 基本赋值操作符(=)
* 读作"被设置为"
#### 1.10.3.2 复合赋值操作符
| 操作符 | 使用方法 |
| --- | ---|
| += | $a+=$b |
| -= | $a-=$b |
| *= | $a*=$b |
| /= | $a/=$b |
| %= | $a%=$b |
| .= | $a.=$b |
```
// 例
$a += 5;
// 等价于
$a = $a + 5;
``` 
#### 1.10.3.3 前置递增递减和后置递增递减
* 前置递增操作符 先递增 再赋值  
* 前置递减操作符 先递减 再赋值
* 后置递增操作符 先赋值 再递增
* 后置递减操作符 先赋值 再递减
```
// 返回 2
$a=1;
echo ++$a;
// 返回 1
$a=1;
echo $a++;
```
#### <font color=red> 1.10.3.4 引用操作符</font>
生成$a副本，再保存到$b
```
<?php
$a = 5;
$b = $a;    // 生成副本，保存在内存其他地方
$a = 7;
echo $b;    // 返回 5
?>
```
引用操作符 &
```
<?php
$a = 5;
$b = &$a;   // 引用操作符
$a = 7;
echo $b;    // 返回 7 $a和$b指向内存相同地址
?>
```
* unset()重置
### 1.10.4 比较操作符
| 操作符 | 名称 |
| --- | --- |
| == | 等于 |
| === | 恒等 |
| != | 不等 |
| !=== | 不恒等 |
| <> | 不等 |
| < | 小于 |
| > | 大于 |
| <= | 小于等于 |
| >= | 大于等于 |
#### 1.10.4.1 等于操作符
* 等于操作符(==)
* 测试两个值是否相等
#### 1.10.4.2 其他比较操作符
* 恒等操作符(===)
* 两边的操作数相等 且 具有相同的数据类型 返回true
### 1.10.5 逻辑操作符
| 操作符 | 名称 | 结果 |
| --- | --- | --- |
| ! | NOT |
| &&  | AND |
| \|\| | OR |
| and | AND |
| or | OR |
| xor | XOR(异或) | 仅有一个true才返回true |
* 优先级: “and”和"or"小于"&&"和"\|\|"
### 1.10.6 位操作符
| 操作符 | 名称 |
| --- | --- |
| & | 按位与 |
| \| | 按位或 |
| ～ | 按位非 |
| ^ | 按位异或 |
| << | 左位移 |
| >> | 右位移 |
### 1.10.7 其他操作符
| 操作符 | 结果 |
| --- | --- |
| new | 初始化类的实例 |
| -> | 访问类的实例 |
#### 1.10.7.1 三元操作符
condition ? value if true : value if false
```
($score >= 60 ? 'Pass' or 'Fail')
```
#### <font color=red> 1.10.7.2 错误抑制操作符</font>
#### <font color=red> 1.10.7.3 执行操作符</font>
#### 1.10.7.4 数组操作符
| 操作符 | 结果 |
|-|-|
| [] | 访问数组元素 |
| => |  |

| 操作符 | 结果 |
| --- | --- |
| + | Union(联合)|
| == | Equality(等价)|
| === | Identity(恒等)|
| != | Inequality(非等价)|
| <> | Inequality(非等价)|
| !== | Non-identity(非恒等)|
#### 1.10.7.5 类型操作符
instanceof 操作符允许检查一个对象是否为特定类的实例
```
<?php
class sampleClass{};
$myobject = new SampleClass();
if ($myobject instanceof sampleClass){
    echo "yes";
}
?>
```
## 1.11 计算表单总金额
使用 PHP 的 Math 库的 number_format()函数
```
$total = 66.6;
echo number_format($total,2);
```
## <font color=red>1.12 理解操作符优先级和结合性</font>
## <font color=red>1.13 使用变量处理函数</font>
### 1.13.1 测试和设置变量类型  
* 变量函数 gettype()  
> 函数原型  
string gettype(mixed var);
```
$a = 56;
echo gettype($a);
```
* 变量函数settype()
> 函数原型  
bool settype(mixed var, string type);
```
$a = 56;
settype($a, 'float');
echo gettype($a);
```
* PHP提供的特定的类型测试函数
1. is_array()
2. is_double()、is_float()、is_real()
3. is_long()、is_int()、is_interger()
4. is_string()
5. is_bool()
6. is_object()
### 1.13.2 测试变量状态
* isset()  
> 函数原型    
bool isset(mixed var[, mixed var[,...]]) 

需要一个变量名称作为参数  
检查一个变量是否存在   
变量存在返回true，否则返回false
* unset()  
>函数原型  
void unset(mixed var[, mixed var[,...]])  
销毁一个传进来的变量
* empty()
> 函数原型  
bool empty(mixed var)  

检查一个变量是否存在，以及它的值是否为非空和非0  
相应的返回true或false
### <font color=red> 1.13.3 变量的重解释</fontx>
通过调用以下函数 实现 转换变量数据类型
int intval(mixed var[, int base=10])
float floatval(mixed var)
string strval(mixed var)
## <font color=red> 1.14 根据条件进行决策</font>
### 1.14.1 if语句 
```
if ($totalqty == 0){
    // code
}
```
### 1.14.2 代码块
使用花括号
```
if ($totalqty == 0){
    // code
}
```
### 1.14.3 else语句
```
// 例1
if ($totalqty == 0){
    // code
} else {
    // code
}
```
嵌套
```
// 例2
if ($totalqty == 0){
    // code
} else {
    if ($tireqty > 0){
        // code
    }
    if ($oilqty > 0){
        // code
    }
    if ($sparkqty > 0){
        // code
    }
}
```
### 1.14.4 elseif语句
```
$tireqty = $_POST['name'];
if ($tireqty < 10) {
    $discount = 0;
} elseif ($tireqty >= 10) && ($tireqty <= 49) {
    $discount = 5;
} ($tireqty >= 50) && ($tireqty <= 99) {
    $discount = 10;
} ($tireqty >= 100) {
    $discount = 15;
}
```
### 1.14.5 switch语句  
HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo</title>
</head>
<body>
    <tr>
        <td>How did you find Bon's?</td>
        <td><select name="find" id="">
        <option value="a">aaa</option>
        <option value="b">bbb</option>
        <option value="c">ccc</option>
        <option value="d">ddd</option>
        </select></td>
    </tr>
</body>
</html>
```
if...elseif...else
```
<?php
$find = $_POST['find'];
if ($find == "a") {
    echo "<p>aaa</p>";
} elseif ($find == "b") {
    echo "<p>bbb</p>";
} elseif ($find == "c") {
    echo "<p>ccc</p>";
} else ($find == "d") {
    echo "<p>ddd</p>";
}
?>
```
switch
```
<?php
$find = $_POST['find'];
switch($find) {
    case "a" :
        echo "<p>aaa</p>";
        break;
    case "b" :
        echo "<p>bbb</p>";
        break;
    case "c" :
        echo "<p>ccc</p>";
        break;
    case "d" :
        echo "<p>ddd</p>";
        break;
    default :
        echo "<p>default</p>";
        break;
} 
?>
```
### <font color=red>1.14.6 比较不同条件</font>
##  <font color=red>1.15 通过迭代实现重复动作</font>
### 1.15.1 while循环 
while( condition ) expression
```
// 例1
$num = 1;
while ($num <= 5){
    echo $num . "<br />";
    $num++;
}
``` 
```
// 例2
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bob's ...</title>
</head>
<body>
    <table style="border: 0px; padding: 3px">
        <tr>
            <td></td>
            <td></td>
        </tr>

        <?php
        $distance = 50;
        while ($distance <= 250){
            echo "<tr>
                <td style=\"text-align: right;\">".$distance."</td>
                <td style=\"text-align: right;\">".($distance / 10)."</td>
                </tr><br />";
            $distance += 50;
        }
        ?>
        
    </table>
</body>
</html>
```
### 1.15.2 for循环和foreach循环
* for循环的基本结构  
for (expression1; condition; expression2)
    expression3;
1. expression1 通常设置 计数器的初始值
2. condition 通常测试 计数器是否达到临界值
3. expression2 通常调整 计数器的值
4. expression3 
```
// 例
<?php
for ($distance = 50; $distance <= 250; $distance += 50) {
    echo "<tr>
        <td style=\"text-align: right;\">".$distance."</td>
        <td style=\"text-align: right;\">".($distance / 10)."</td>
        </tr>\n";}
?>
```
* 可使用可变变量和for循环语句来遍历多个表单域  
* 通过动态地创建变量名称，可依次访问每个表单域
```
// 若有名为 name1、name2、name3等的表单域
for ($i=0; $i<=$numnames; $i++){
    $temp = "name$i";
    echo htmlspecialchars($$temp).'<br />';
}
```
### 1.15.3 do...while结构
do...while语句的常见结构:
```
do
    expression;
while( condition )
```
do..while循环中的语句或语句块至少会执行一次
```
// 例
$num = 100;
do {
    echo $num . "<br />";
} while ($sum < 1 );
```
## 1.16 从控制结构或脚本中跳出
* break  
终止一个循环 从循环体后面的第一条语句处开始执行
* continue  
跳到下一次循环
* exit  
结束整个PHP脚本的执行
```
// 例
if ($totalqty == 0){
    echo "Something right here!";
    exit;
}
```
## <font color=red>1.17 使用其他控制结构语法</font>
## <font color=red>1.18 使用declare</font>
## <font color=red>1.19 下一章</font>