### jQuery和js加载模式
1. 原生JS和jQuery入口函数的加载模式不同
   - 原生JS会等到DOM元素加载完毕，并且图片也加载完毕才会执行
   - jQuery会等到DOM元素加载完毕，但不会等到图片也加载完毕就会执行
   * 原生的JS如果编写了多个入口函数，后面编写的会覆盖前面写的 *
   * jQuery中编写多个入口函数，后面的不会覆盖前面的 *

*******

### jQuery入口函数其他写法
1. 第一种写法：
```
$(document).ready(function () {
    alert("hello siyang");
});
```

2. 第二种写法：
```
jQuery(document).ready(function () {
    alert("hello siyang");
});
```

3. 第三种写法：(推荐)
```
$(function () {
    alert("hello siyang");
});
```

4. 第四种写法：
```
jQuery(function () {
    alert("hello siyang");  
});
```

*******

### jQuery冲突问题
1. 释放$的使用权：
`jQuery.noConflict();`

*释放操作必须在编写其他jQuery代码之前编写；释放之后就不能再使用$，改为使用jQuery*
2. 自定义一个访问符号：
```
var nj = jquery.noConflict();
nj(function () {
    alert("hello siyang");  
});
```

*******

### jQuery核心函数
$(); 就代表调用jquery的核心函数
1. 接收一个函数
```
$(function () {
    alert("hello siyang");  
    2. 接收一个字符串
       2.1 接收一个字符串选择器
       *返回一个jQuery对象，对象中保存了找到的DOM元素*
       ```
       var $box1 = $(".box1");
       var $box2 = $("#box2");
       console.log($box1);
       console.log($box2);
       ```
       2.2 接收一个字符串代码片段
       * 返回一个jQuery对象，对象中保存了创建的DOM元素 *
       ```
       var $p = $("<p>我是段落</p>");
       console.log($p);
       ```
    3. 接收一个DOM元素
    * 会被包装成一个jQuery对象返回给我们 *
    ```
    var span = document.getElmentByTagName("span")[0];
    console.log(span);
    var $span = $(span);
    console.log($span);
    ```
});
```

*******

### jQuery对象
1. jQuery对象是一个伪数组
2. 有0到length-1的属性，并且有length属性

*******

静态方法：
直接添加到类上面的就是静态方法；通过类名来调用
实例方法：
添加到类的原型上面的实例方法；通过类的实例来调用

*******

### jQuery-each方法
1. 原生的forEach方法只能遍历数组，不能遍历伪数组
```
var arr = [1, 3, 5, 7, 9];
arr.forEach(function (value, index) {
    console.log(index, value);
});
```
第一个参数：遍历到的元素；
第二个参数：当前遍历到的索引

2. 利用jQuery的each静态方法遍历数组,则可以遍历伪数组
```
var arr = [1, 3, 5, 7, 9];
$.each(arr, function (index, value) {
    console.log(index, value);
});

var obj = {0:1, 1:3, 2:5, 3:7, 4:9, length:5};
$.each(obj, function (index, value) {
    console.log(index, value);
});
```
第一个参数：当前遍历到的索引；
第二个参数：遍历到的元素

*******

### jQuery-map方法
1. 利用原生JS的map方法遍历，和原生的forEach一样不能遍历伪数组
```
var arr = [1, 3, 5, 7, 9];
arr.map(function (value, index, array) {
    console.log(index, value, array);
});
```
第一个参数：当前遍历到的元素；
第二个参数：当前遍历到的索引；
第三个参数：当前被遍历的数组.

2. 和jQuery中的each静态方法一样，map静态方法也可以遍历伪数组
```
var arr = [1, 3, 5, 7, 9];
$.map(arr, function (value, index) {
    console.log(index, value);
});
```
```
var obj = {0:1, 1:3, 2:5, 3:7, 4:9, length:5};
$.each(obj, function (index, value) {
    console.log(index, value);
});
```
第一个参数：当前遍历到的数组；
第二个参数：每遍历一个元素之后执行的回调函数。

回调函数的参数：
第一个参数：遍历到的元素；
第二个参数：遍历到的索引。

*jQuery中的each方法静态方法和map静态方法的区别：*

*each静态方法默认的返回值就是，遍历谁就返回谁；
map静态方法默认的返回值是一个空数组；*

*each静态方法不支持在回调函数中对遍历的数组进行处理；map静态方法可以在回调函数中通过return对遍历的数组进行处理，然后生成一个新的数组返回*

*******

### jQuery其他静态方法
1. $.trim();
作用：去除字符串两端的空格；
参数：需要去除空格的字符串；
返回值：去除空格之后的字符串
```
var str = "   siyang    ";
var res = $.trim(str);
```
2. $.isWindow();
作用：判断传入的对象是否是window对象；
返回值：ture/false;
```
var arr = [1, 3, 5, 7, 9];
var arrlike = {0:1, 1:3, 2:5, 3:7, 4:9, length:5};
var obj = {"name":"lnj", age:"33"};
var fn = function() {};
var w = window;
var res = $.isWindow(arr||arrlike||obj||fn||w);
console.log(res); //false,false,false,false,true
```
3. $.isArray();
作用：判断传入的对象是否是window对象；
返回值：true/false;
```
var arr = [1, 3, 5, 7, 9];
var arrlike = {0:1, 1:3, 2:5, 3:7, 4:9, length:5};
var res = $.isArrray(arr||arrlike);
console.log(res); //true,false
```
4. $.isFunction();
作用：判断传入的对象是否是一个函数；
返回值：true/false;
*jquery框架本质上是一个函数*
```
var arr = [1, 3, 5, 7, 9];
var arrlike = {0:1, 1:3, 2:5, 3:7, 4:9, length:5};
var obj = {"name":"lnj", age:"33"};
var fn = function() {};
var w = window;
var res = $.isFunction(arr||arrlike||obj|| fn ||w|| jQuery );
console.log(res); //false,false,false,true,false,true
```

*******

### jQuery-holdReady方法
$.holdReady(true / false);
作用：暂停 / 恢复ready执行
```
$.holdReady(true);
$(document).ready(function () {
    alert("ready");
});
```

*******

### 