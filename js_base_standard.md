# JAVASCRIPT编码规范

CSS相关文件书写风格及注意事项规范


## 缩进

统一**4个空格**缩进

#### 影响

（无）

#### 例子

（无）

#### 重要性

推荐


## 一般变量函数命名

1. 变量（属性）、函数（方法）采用驼峰命名
2. 变量（属性）应该以**名词**开头，函数（方法）应该是**动词+名词**

#### 影响

（无）

#### 例子

```js
//推荐
var count = 10;
var myName = 'Nicholas';
var found = true;
//不推荐
var getCount = 10;
var isFound = true;
```

```js
//推荐
function getName() {
    return myName;
}
//不推荐
function theName() {
    return myName;
}    
```

#### 重要性

推荐


## 常量命名

全部大写，单词之间用`_`下划线连接

#### 影响

（无）

#### 例子

```js
// 推荐
var MAX_COUNT = 10;
var URL = 'http://www.foo.com';
```

#### 重要性

推荐


## 构造函数

命名规范与变量相同，但第一个字母必须大写。

#### 影响

（无）

#### 例子

```js
// 推荐
function Person(name){
    this.name = name;
}
Person.prototype.sayName = function(){
    alert(this.name);
}
var me = new Person('foo');
```

#### 重要性

推荐


## 条件判断

1. 在任何可能的情况下，使用`===`而不是`==`判断
2. 布尔值直接判断

#### 影响

javascript的隐式类型转换错综复杂，使用不当会造成隐藏bug，而使用等等于则能有效避免这个问题

#### 例子

```js
// 不推荐
if(variable == 0){}
if(variable == false){}
// 推荐
if(variable === 0){}
if(!variable){}
```

#### 重要性

必须


## 字符串

总是使用单引号`'`，而不是双引号`"`

#### 影响

（无）

#### 例子

```js
// 不推荐
var html = "<a href=\"\"></a>";
// 推荐
var html = '<a href=""></a>';
```

#### 重要性

推荐


## 分号

总是在语句结束后加分号`;`，非函数的大括号`}`结束可除外

#### 影响

对于以下代码会出现错误：

```js
function func(){
    // ...
}

(function(){
    // ...
}());
```

#### 例子

（无）

#### 重要性

必须


## CSS分离

CSS与JavaScript关系紧密，有时经常将样式数据与JavaScript混写，通过JavaScirpt直接操作DOM元素的`style`属性来修改CSS数据。

这样的做法有问题，样式信息不是放在CSS文件中而是写在JavaScript文件。

将CSS从JavaScript分离是指把所有的样式信息放在CSS文件，当需要通过JavaScript修改元素样式时，最好的办法是操作CSS的`className`。

#### 影响

js主管交互，css主管样式，如果把样式写在js中不利于单独维护

#### 例子

```js
//不推荐
element.style.color = 'red';
element.style.left = '10px';
element.style.top = '100px';
element.style.visibility = 'visible';

element.style.cssText = 'color: red; left: 10px; top: 100px; visibility: hidden';    
```
```js
// 推荐
element.className += ' dialog';    
```
css文件：
```css
.dialog {
    color: red;
    left: 10px;
    top: 100px;
    visibility: visible;
}
```

#### 重要性

推荐


## HTML分离

不应将html嵌入js代码中

#### 影响

不利于维护

#### 例子

```js
// 不推荐
var div = document.getElementById('my-div');
div.innerHTML = '<h3>Error</h3><p>Invalid e-mail address.</p>';    
```

#### 重要性

推荐


## 严格模式

全项目使用严格模式`use strict`;

#### 影响

减少意外错误发生

#### 例子

（无）

#### 重要性

推荐


## 全局变量

避免全局变量污染

#### 影响

1. 容易造成命名冲突
2. 代码耦合高，不利于维护

#### 例子

（无）

#### 重要性

必须


## 事件绑定

事件绑定函数应该与业务逻辑分离

#### 影响

不利于维护

#### 例子

```js
// 不推荐
$(target).on('click', function (event) {
    var popup = document.getElementById('popup');
    popup.style.left = event.clientX + 'px';
    popup.style.top = event.clientY + 'px';
    popup.className = 'reveal';
});

//推荐
//事件处理逻辑
var MyApplication = {
    // other...
    showPop: function(x ,y){
        var popup = document.getElementById('popup');
        popup.style.left = x + 'px';
        popup.style.top = y + 'px';
        popup.className = 'reveal';            
    }
};
//事件绑定
$(target).on('click', function(event){
    //调用事件处理函数
    MyApplication.showPop(event.clientX ,event.clientY);
});
```

#### 重要性

推荐


## 配置分离

配置数据应从业务逻辑代码中抽离

#### 影响

不利于维护

#### 例子

```js
//不推荐
//将配置信息硬编码写入源码中
function validate(value){
    if(!value){
        alert('Invalid value');
        location.href = '/errors/invalid.php';
    }
}
function toggleSelected($element){
    if($element.hasClass('selected')){
        $element.removeClass('selected');
    }else{
        $element.addClass('selected');
    }
}

//推荐
//配置信息
var config = {
    MSG_INVALID_VALUE: 'Invalid value',
    URL_INVALID: '/errors/invalid.php',
    SELECTED_CLASSNAME: 'selected'
};
function validate(value){
    if(!value){
        alert(config.MSG_INVALID_VALUE);
        location.href = config.URL_INVALID;
    }
}
function toggleSelected($element){
    var selected = config.SELECTED_CLASSNAME;
    if($element.hasClass(selected)){
        $element.removeClass(selected);
    }else{
        $element.addClass(selected);
    }
}
```

#### 重要性

推荐


## 变量声明与使用

变量（函数也是变量）声明、复制、使用都需要按顺序

#### 影响

javascript语法存在hoisting（声明提升），会先扫描一遍变量声明，再执行，这种有碍正常思维

#### 例子

```js
// 不推荐
var myname = 'global';//全局变量
func();
function func() {
    alert(myname);//'undefined'
    var myname = 'local';
    alert(myname);//'local'
}
```

#### 重要性

推荐


## prototype

不要扩展内置对象原型

#### 影响

可能会覆盖原生属性

#### 例子

```js
// 不推荐
if(typeof Object.prototype.clone === 'undefined' ) {
    Object.prototype.clone = function () {
        //...
    };
}
```

#### 重要性

推荐


## for-in遍历

对对象进行遍历属性时，最好使用`hasOwnProperty`进行检验

#### 影响

对象可能存在继承的属性，从而可能会造成bug

#### 例子

```js
// 不推荐
for (var i in man) {
    console.log(i, ':', man[i]);
}
// 推荐
for (var i in man) {
    if (man.hasOwnProperty(i)) {
        console.log(i, ':', man[i]);
    }
}
```

#### 重要性

推荐


## eval

避免使用eval

#### 影响

容易出错，容易埋坑

#### 例子

```js
//不推荐
var code = 'alert("eval")';
eval(code);

var property = 'name';
alert(eval('obj.' + property));

setTimeout('myFunc(1)', 1000);
```

#### 重要性

推荐


## parseInt

第二个参数`10`必须添加

#### 影响

不添加在ie7-下会输出0

#### 例子

```js
// 不推荐
var month = '06M';
month = parseInt(month);//存在兼容性问题IE7以下输出0

//推荐
month = parseInt(month, 10);//指定将字符串转换成十进制数,正确输出6
```

#### 重要性

必须


## url编码

在拼接url时，查询参数必须进过编码

#### 影响

查询参数值中存在`?&=`等字符时对值有影响

#### 例子

```js
// 不推荐
var url = location.href + '?id=' + id;

// 推荐
var url = location.href + '?id=' + encodeURIComponent(id);
```

#### 重要性

必须
