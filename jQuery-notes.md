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

### jQuery内容选择器
1. :empty
作用：找到既没有文本内容也没有子元素的指定元素
```
var $div = $("div:empty");
console.log($div);
```

2. :parent
作用：找到有文本内容或有子元素的指定元素
```
var $div = $("div:parent");
```

3. :contains
作用：找到包含指定文本内容的指定元素
```
var $div = $("div:contains('我是div')")；
```

4. :has(selector)
作用：找到包含指定子元素的指定元素
```
var $div = $("div:has('span')");
```

******

### attr和removeAttr方法
1. 作用：获取或者设置属性节点的值，可以传递一或两个参数；
如果传递一个参数，代表获取属性节点的值，
如果传递两个参数，代表设置属性节点的值
```
<span class="span1 name="it666"></span>
<span class="span2 name="lnj"></span>
$("span").attr("class");
*如果是获取，无论找到多少个元素，都只会返回第一个元素指定的属性节点的值*
$("span").attr("class", "box");
*如果是设置，找到多少个元素就会设置多少个元素；如果设置的属性节点不存在，那么系统会自动新增*
```

2. removeAttr(name)
作用：删除属性节点
```
<span class="span1 name="it666"></span>
<span class="span2 name="lnj"></span>
$("span").removeAttr("class");
```
*会删除所有找到元素指定的属性节点，如果要删除多个，则用空格隔开即可*

*******

### prop和removeProp方法
1. prop
```
$("span").eq(0)指找到第一个span标签
$("span").eq(0).prop("demo", "it666");
新增一个demo属性，并赋值为it666
```
*特点和attr方法一致，除此之外，还能操作属性节点*
2.removeProp
*特点和removeAttr方法一致*

**官方推荐在操作属性节点时，具有true和false两个属性的属性节点，如checked，selected或者disabled，使用prop()，其他的使用attr()**

*******

### jquery类操作相关方法
1. addClass(class||fn)
作用：添加一个类
如果要添加多个，多个类名之间用空格隔开即可
2. removeClass( [class||fn] )
作用：删除一个类
如果想删除多个，多个类名之间用空格隔开即可
3. toggleClass( class||fn[,sw] )
有就删除，没有就添加

********

### jQuery文本值相关操作
1. html( [val|fn] )
和原生JS中的innerHTML一模一样
2. text( [val|fn] )
和原生JS中的innerText一模一样
3. val( [val|fn|arr] )
```
<input></input>
$("input").val("请输入内容");
这时输入框中会显示“请输入内容”
```

*******

### jQuery事件
事件绑定有两种方式：
1. eventName(fn);
```
$("button").click(function () {
    alert("hello siyang");
});
```
*编码效率略高/部分事件jQuery没有实现，所以不能添加*
2.on(eventName,fn);
```
$("button").on("click", function() {
    alert("hello siyang");
});
```
*编码效率略低/所有js事件都能添加*

**两种方法可以添加多个相同或者不同类型的事件，不会覆盖**

事件解绑
off方法：
如果不传递参数，会移除所有的事件
`$("button").off();`
如果传递一个参数，会移除所有指定类型的事件
`$("button").off("click");`
如果传递两个参数，会移除所有指定类型的指定事件
`$("button").off("click", test1);`


*******

### jQuery事件冒泡和默认行为
1. 什么是事件冒泡
2. 如何阻止事件冒泡：在下级/儿子事件绑定处加上“return false;”或者“event.stopPropagation();”
3. 什么是默认行为
4. 如何阻止默认行为：在事件绑定处加上“return false;”或者“event.preventDefault();”

*******

### jquery事件自动触发
1. trigger:如果用trigger自动触发事件，会触发事件冒泡，会触发默认行为；
2. triggerHndleer：如果利用triggerHndleer自动触发事件，不会触发事件冒泡，不会触发默认行为。
```
<div class="father"></div>
$(".father").trigger("click");
$(".father").triggerHandler("click");
```

*******

### jQuery自定义事件
必须满足两个条件：
1. 事件必须是通过on绑定的
2. 事件必须通过trigger来触发

*******

### jQuery事件命名空间
想要事件的命名空间有效，必须满足两个条件：
1. 事件是通过on来绑定的
2. 通过trigger触发事件
```
$(".father").on("click.siyang", function () {
    alert("father click1");
})
$(".father").on("click", function () {
    alert("father click2");
})
$(".son").on("click.siyang", function () {
    alert("son click1");
})
```
`$(".son").trigger("click.siyang");`
//son click1
//father click1

*利用trigger触发子元素带命名空间的事件，那么父元素带相同命名空间的事件也会被触发，而父元素没有命名空间的事件不会被触发*

`$(".son").trigger("click");`
//son click1
//father click1
//father click2

 *利用trigger触发子元素不带命名空间的事件，那么子元素所有相同类型的事件和父元素所有相同类型的事件都会被触发*

*******

### jquery事件委托
什么是事件委托：请别人帮忙做事情，然后将做完的结果反馈给我们
```
<ul>
    <li>我是第1个li<li>
    <li>我是第2个li<li>
    <li>我是第3个li<li>
</ul>
<button>新增一个li</button>
$("ul").delegate("li", "click", function() {
    console.log($(this).html());
});
```

*******

## 移入移出事件
1. mouseover/mouseout：子元素被移入移出也会触发父元素的事件
2. mouseenter/mouseleave：子元素被移入移出不会触发父元素的事件(推荐使用)
3. 既监听移入又监听移出事件的方法：
hover(function(){}, function(){})
若输入两个参数：第一个参数表移入，第二个参数表移出
若输入一个参数，则既表移入又表移出