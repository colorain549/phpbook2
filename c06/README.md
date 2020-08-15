# 第六章 面向对象特性
## 6.1 理解面向对象概念
### 6.1.1 类和对象
> <font color=red>略</font>
### 6.1.2 多态性
> <font color=red>TODO</font>
### 6.1.3 继承
> <font color=red>TODO</font>
## 6.2 在PHP中创建类、属性和操作
### 6.2.1 类结构
类定义
```
class classname {
    // code
}
```
创建类的属性
```
class classname {
    public $attr1;
    public $attr2;
}
```
创建类的方法
```
class classname {
    function operation1 (){
        // code
    }
    function operation2 ($para1, $para2){
        // code
    }
}
```
### 6.2.2 构造函数
* 当创建一个对象时，对象的构造函数将被调用
* 通常，用于 设置属性的初始值 或者 创建该对象需要的其他对象
```
<?php
class MyClass {
    function __construct($para){
        echo $para . "<br />";
    }
}
?>
```
### 6.2.3 析构函数
* 在销毁一个类之前被调用执行 
* 完成一些操作或实现一些功能
* 操作或功能通常在所有对该类的引用都被重置或超出作用域时自动发生
* 析构函数 不能 带有任何参数
## 6.3 类的实例化
```
<?php
class MyClass {
    function __construct($para){
        echo $para . "<br />";
    }
}
$a = new Myclass("fisrtPara");
$b = new MyClass("secondPara");
// 警告，创建了没有参数数的对象
$c = new MyClass();
?>
```
```
<?php
class MyClass {
    function __construct($para = "defaultPara"){
        echo $para . "<br />";
    }
}
$a = new Myclass("fisrtPara");
$b = new MyClass("secondPara");
$c = new MyClass();
?>
```
## 6.4 使用类属性
```
// 类中设置和访问
class classname {
    public $attr;
    function operaition($para){
        // 类中设置
        $this->$attr = $para;
        // 类中访问
        echo $this->$attr;
    }
}
```

```
// 类外访问
class classname {
    public $attr;
}
$a = new classname();
$a->attr = "value";
echo $this->attr;
```
## 6.5 调用类操作
```
class classname {
    function operation(){
        // code
    }
    function operation($para1, $para2){
        // code
    }
}
$a = new classname();
$a -> operaiton();
$a -> operaiton($para1, $para2);
// 如果操作有返回值 通过赋值获得返回数据
$x = $a -> operation();
$y = $b -> operaiton($para1, $para2);
```
## 6.6 使用private和public关键字控制访问
> <font color=red>略</font>
## 6.7 编写访问器函数
> <font color=red>略</font>
## 6.8 在PHP中实现继承
> <font color=red>略</font>
### 6.8.1 通过继承使用private和protected控制可见性
> <font color=red>略</font>
### 6.8.2 覆盖
> <font color=red>略</font>
### 6.8.3 使用final关键字禁止继承和覆盖
> <font color=red>略</font>
### 6.8.4 理解多重继承
> <font color=red>略</font>
### 6.8.5 实现接口
> <font color=red>略</font>
## 6.9 使用Trait
> <font color=red>略</font>
## 6.10 类设计
> <font color=red>略</font>
## 6.11 编写自定义类的代码
> <font color=red>略</font>
## 6.12 理解PHP面向对象高级功能
### 6.12.1 使用类级别常量
```
<?php
// 类级别常量 可在不需要初始化该类的情况下使用
class Math {
    const PI = 3.14;
}
echo "Math::PI = " . Math::PI;
?> 
```
### 6.12.2 实现静态方法
```
class Math {
    static function squared($input=0){
        return $input * $input;
    }
}
echo "Math::squared(6) = " . Math::squared(6)
```
### 6.12.3 检查类类型和类型提示
> <font color=red>略</font>
### 6.12.4 延迟静态绑定

### 6.12.5 对象克隆
### 6.12.6 使用抽象类
### 6.12.7 使用__call()重载方法
### 6.12.8 使用__autoload()方法
### 6.12.9 实现迭代器和迭代
### 6.12.10 生成器
### 6.12.11 将类转换成字符串
### 6.12.12 使用反射API
### 6.12.13 名称空间
### 6.12.14 使用子名称空间
### 6.12.15 理解全局名称空间
### 6.12.16 名称空间的导入和别名
## 6.13 下一章
