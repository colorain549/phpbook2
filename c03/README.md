# 第三章 使用数组
## 3.1 什么是数组
* 数组 是 用来存储 一系列变量值的 命名区域
* 存储在数组中的值 称为 数组元素
* 每个数组元素有一个相关的索引/关键字/键 用于访问元素
## 3.2 数字索引数组
### 3.2.1 数字索引数组的初始化
使用array()函数
```
// 使用array()函数
$products = array('Tires', 'Oil', 'Spark Plugs');
```
使用"[]"字符
```
// 使用"[]"字符
$products = ['Tires', 'Oil', 'Spark Plugs'];
```
使用range()函数
```
// 创建一个 从1到10的 数字数组
$numbers = range(1, 10);
```
```
// 创建一个 从1到10的 奇数数组
$odds = range(1, 10, 2);
```
```
// 创建一个 从a到z的 字符数组
$letters = range('a', 'z');
```
```
// 创建一个 从a到z的 相隔一个字符的 字符数组
$letters = range('a', 'z', 2);
```
### 3.2.2 访问数组内容
替换元素
```
$products = ['Tires', 'Oil', 'Spark Plugs'];
$products[0] = 'Fuses';
```
增加元素
```
$products = ['Tires', 'Oil', 'Spark Plugs'];
$products[3] = 'Fuses';
```
显示数组内容
```
$products = ['Tires', 'Oil', 'Spark Plugs'];
echo "products[0] products[1] products[2] products[3]"; 
```
创建数组
```
// 先创建只含一个元素的数组 再往数组添加新的数值
$products[0] = 'Tires';
$products[1] = 'Oil';
$products[2] = 'Spark plugs';
```
### 3.2.3  使用循环访问数组
使用 for 循环 显示 有序数字做索引的 数组
```
$products = ['Tires', 'Oil', 'Spark Plugs'];
for ($i = 0; $i<3; $i++) {
    echo $products[$i] . PHP_EOL;
}
```
使用 foreach 循环 打印数组
```
$products = ['Tires', 'Oil', 'Spark Plugs'];
foreach($products as $current){
    echo $current . PHP_EOL;
}
```
## 3.3 使用不同索引的数组
### 3.3.1 初始化数组
```
// 创建一个 指定键和值的数组
$prices = ['Tires'=>100, 'Oil'=>10, 'Spark Plugs'=>4];
```
### 3.3.2 访问数组元素
```
// 创建只有一个元素的数组 再加上另外的元素
$prices = array('Tires'=>100);
$prices['Oil'] = 10;
$prices['Spark Plugs'] = 4; 
```
```
// 创建数组
$prices['Tires'] = 100;
$prices['Oil'] = 10;
$prices['Spark Plugs'] = 4; 
```
### 3.3.3 使用循环语句
```
// 使用 foreach 打印 含键和值的 数组
$prices = ['Tires'=>100, 'Oil'=>10, 'Spark Plugs'=>4];
foreach ($prices as $key => $value) {
    echo $key . " - " . $value . "<br/>";
}
```
```
// 使用 each()结构 列出 数组内容
$prices = ['Tires'=>100, 'Oil'=>10, 'Spark Plugs'=>4];
while ($element = each($prices)){
    echo $element['key'] . " - " . $element['value'];
    echo "<br />";
}
```
```
// 使用list()结构 和 each()结构 打印数组
$prices = ['Tires'=>100, 'Oil'=>10, 'Spark Plugs'=>4];
while(list($product, $price) = each($price)){
    echo $product . " - " . $price . "<br />";
}
```
```
// 使用reset()函数将当前元素设置为数组的开始
$prices = ['Tires'=>100, 'Oil'=>10, 'Spark Plugs'=>4];
reset($prices);
while(list($product, $price) = each($prices)){
    echo $product . " - " . $price . "<br />";
}
```
## 3.4 数组操作符
| 操作符| 名称  | 示例  |
| ---- | ----  | ----  |
| + | 联合 | $a + $b |
| == | 等价 | $a == $b |
| === | 恒等 | $a === $b |
| != | 不等价 | $a != $b |
| <> | 不等价 | $a <> $b |
| !== | 不恒等 | $a !== $b |
## 3.5 多维数组
创建二维数组
```
$products = array( array('TIR', 'Tires', 100),
                   array('OIL', 'Oil', 10),
                   array('SPK', 'Spark Plugs', 4));
```
显示数组内容
```
// 顺序访问每个数组
$products = array( array('TIR', 'Tires', 100),
                   array('OIL', 'Oil', 10),
                   array('SPK', 'Spark Plugs', 4));
echo '|' . $product[0][0] . '|' . $product[0][1] . '|' . $product[0][2] . '<br />';
echo '|' . $product[1][0] . '|' . $product[1][1] . '|' . $product[1][2] . '<br />';
echo '|' . $product[2][0] . '|' . $product[2][1] . '|' . $product[2][2] . '<br />';
```
```
// 双重 for 循环
$products = array( array('TIR', 'Tires', 100),
                   array('OIL', 'Oil', 10),
                   array('SPK', 'Spark Plugs', 4));
for($row = 0; $row < 3; $row++){
    for($col = 0; $col < 3; $col++){
        echo '|' . $products[$row][$col];
    }
    echo '|<br />';
}
```
创建含列名称的二维数组
```
$products= array(array('Code' => 'TIR',
                       'Description => 'Tires',
                       'Price => 100'
                       ),
                array('Code' => 'OIL',
                       'Description => 'Oil',
                       'Price => 10'
                       ),
                array('Code' => 'TIR',
                       'Description => 'Tires',
                       'Price => 4'
                       ),
                );  
```
使用 for 循环遍历 显示内容
```
$products= array(array('Code' => 'TIR',
                       'Description => 'Tires',
                       'Price => 100'
                       ),
                array('Code' => 'OIL',
                       'Description => 'Oil',
                       'Price => 10'
                       ),
                array('Code' => 'TIR',
                       'Description => 'Tires',
                       'Price => 4'
                       ),
                );  
for ($row = 0; $row < 3; $row++){
    echo '|' . $products[$row]['Code'] .
         '|' . $products[$row]['Code'] .
         '|' . $products[$row]['Code'] . '|<br />';
}
```
创建三维数组
```
$categories = array(array(array('CAR_TIR', 'Tires', 100),
                    array(array('CAR_OIL', 'Oil', 10),
                    array(array('CAR_SPK', 'Spark Plugs', 4),
                    ),
              array(array(array('VAN_TIR', 'Tires', 120),
                    array(array('VAN_OIL', 'Oil', 12),
                    array(array('VAN_SPK', 'Spark Plugs', 5),
                    ),
              array(array(array('TRK_TIR', 'Tires', 150),
                    array(array('TRK_OIL', 'Oil', 15),
                    array(array('TRK_SPK', 'Spark Plugs', 6),
                    ),
            );
```
使用嵌套的 for 循环 显示内容
```
$categories = array(array(array('CAR_TIR', 'Tires', 100),
                    array(array('CAR_OIL', 'Oil', 10),
                    array(array('CAR_SPK', 'Spark Plugs', 4),
                    ),
              array(array(array('VAN_TIR', 'Tires', 120),
                    array(array('VAN_OIL', 'Oil', 12),
                    array(array('VAN_SPK', 'Spark Plugs', 5),
                    ),
              array(array(array('TRK_TIR', 'Tires', 150),
                    array(array('TRK_OIL', 'Oil', 15),
                    array(array('TRK_SPK', 'Spark Plugs', 6),
                    ),
            );
for ($layer = 0; $layer < 3; $layer++){
    echo 'Layer'.$layer."<br />";
    for ($row = 0; $row < 3; $row++){
        for($col = 0; $col < 3; $col++){
            echo '|'.$categories[$layer][$row][$col];
        }
        echo '|<br />';
    }
}
```
## 3.6 数组排序
### 3.6.1 使用sort()函数
```
// 按字母升序
$products = array('Tires', 'Oil', 'Spark Plugs');
sort($products)
```
```
// 按数字升序
$prices = array(100, 10, 4);
sort($prices)
```
> sort()函数区分字母大小写 大写字母在小写字母前面  

> sort()函数的第二个参数:
> 1. SORT_REGULAR(默认值)
> 2. SORT_NUMERIC(按数字？？？)
> 3. SORT_STRING(按字符串？？？)  
> 4. SORT_LOCALE_STRING 
> 5. SORT_NATURAL(相当于natsort()函数)
> 6. SORT_FLAG_CASE(忽略大小写)  
```
例  按数字 2小于12  
    按字符串 '12'小于'2' 
```
### 3.6.2 使用asort()函数和ksort()函数对数组排序
```
// 按值(value)排序
$prices = array('Tires'=>100, 'Oil'=>10, 'Spark Plugs');
asort($prices)
```
```
// 按键(key)排序
$prices = array('Tires'=>100, 'Oil'=>10, 'Spark Plugs');
ksort($prices)
```
### 3.6.3 反向排序
| 函数 | 说明 |
| ---- | ---- |
| rsort() | 按字母或数字降序 |
| arsort()| 按值(value)降序 |
| krsort()| 按键(key)降序 |
## 3.7 多维数组排序
### 3.7.1 使用array_multisort()函数
```
// 按数组中每个子数组的第一个元素按常规升序进行排序
$products = array(array('OIL', 'Oil', 100),
                  array('SPK', 'Spark Plugs', 10),
                  array('TIR', 'Tires', 4));
array_multisort();
```
### 3.7.2 用户定义排序
| 函数 | 说明 |
| ---- | ---- |
| usort() | 略 |
| uasort() | 略 |
| uksort() | 略 |
### 3.7.3 自定义排序反序
> 略
## 3.8 对数组进行重新排序
| 函数 | 说明 |
| ---- | ---- |
| shuffle() | 将数组各元素进行随机排序 |
| array_reverse() | 按原来数组顺序的反向排序 |
### 3.8.1 使用shuffle()函数
```
略
```
### 3.8.2 逆序数组内容
| 函数 | 说明 |
| ---- | ---- |
| array_reverse() | 反向数组顺序 |
| array_push() | 将每个新元素添加到数组末尾 |
| array_pop() | 删除并返回数组末尾的一个元素 |
## 3.9 从文件载入数组
> 略
### 3.10.1 在数组中浏览: each()、current()、reset()、end()、next()、pos()和prev()
### 3.10.2 对数组每一个元素应用函数: array_walk()
### 3.10.3 统计数组元素个数: count()、sizeof()、array_count_values()
### 3.10.4 将数组转换成标量变量: extract()
## 3.11 进一步学习
[参阅PHP的在线手册](http://www.php.net/array)
## 3.12 下一章
> 略