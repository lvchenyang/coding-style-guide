# [1. 代码风格](#codeStyle)
## [1.1 编码](#encoding)
## [1.2 结构](#structure)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.1 缩进](#indent)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.2 空格](#space)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.3 换行](#wrap)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.4 语句](#line)
## [1.3 命名](#name)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.3.1 文件命名](#fileName)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.3.2 对象命名](#objectName)
## [1.4 注释](#notes)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.4.1 单行注释](#singleNotes)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.4.2 多行注释](#multiNotes)


# [2. 语言特性](#language)
## [2.1 变量](#variable)
## [2.2 控制语句](#contralStatment)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.2.1 if/else](#ifElse)
### &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.2.2 while/for](#whileFor)
## [2.3 字符串](#string)
## [2.4 数组](#array)
## [2.5 函数](#function)
## [2.6 面向对象](#object)

# [3.jQuery](#jQuery)


# <span id="codeStyle">1. 代码风格</span>
## <span id="encoding">1.1 编码</span>
JavaScript文件的编码建议使用UTF-8格式。
## 1.2 结构
### 1.2.1 缩进
* 使用4个空格作为缩进，禁止使用Tab和两个空格进行缩进
```javascript
//bad
function getType() {
  var name;
}
//good
function getType() {
    var name;
}
```
* 在进行链式调用时使用缩进，并将除第一行以外的`.`放在每行第一个字符
```javascript
//bad
$('#items').find('.selected').highlight().end().find('.open').updateCount();

//bad
$('#items').find('.selected').
            highlight().
            end().
            find('open').
            updateCount();
            
//good
$('#items').find('.selected')
           .highlight()
           .end()
           .find('open')
           .updateCount();
```
###### 1.2.2 空格






对象
----

* 使用直接量创建对象

```javascript
var obj = {}
```

* 不要使用保留字作为键名

> 保留字作为关键字不兼容IE8（使用同义词替换需要使用的保留字）

```javascript
//bad
var superman = {
    class: 'alien'
}

//good
var superman = {
    type: 'alien'
}
```

数组
---
* 使用直接量创建数组
```javascript
//bad
var items = new Array();

//good
var items = [];
```
* 使用`push`向数组元素赋值
```javascript
var arr = [];
//bad
arr[0] = 'item';
//good
arr.push('item');
```
* 拷贝数组时，使用`slice`函数
```javascript
var itemsCopy = [];
var len = items.length;
//bad
for(var i =0; i < len; i++){
    itemsCopy[i] = item[i];
}
//good
itemsCopy = items.slice();
```

字符串
---
* 使用单引号`''`包裹字符串
```javascript
//bad
var name = "Tom"
//good
var name = 'Tom'
```
* 超过100个字符的字符串应该使用连接符写成多行

函数
---
* 三种函数表达式
```javascript
//匿名函数表达式
var anonymous = function(){
    //TODO
}
//命名函数表达式
function named(){
    //TODO
}
//立即调用函数表达式（IIFE）
(function(){
    //TODO
})();
```
* 禁止将函数的形参命名为`arguments`。
```javascript
//bad
function nope(name, options, arguments){
    //TODO
}

//good
function yup(name, options, args){
    //TODO
}
```

属性
---
* 使用`.`来访问属性

```javascript
var person = {
    name: 'Jder',
    age: '26'
}
//bad
var name = person['name'];
var age = person['age'];

//good
var name = person.name;
var age = person.age;
```

变量
---
* 永远使用`var`关键字来声明变量
> 注：避免污染全局变量
```javascript
//bad
person = {};

//good
var person = {} 
```
* 使用`var`来声明每一个变量
```javascript
//bad
var items = [],
    name = 'Jder',
    age = 26;

//good
var items = [];
var name = 'Jder';
var age = 26;
```
* 最后再声明为赋值的变量
```javascript
//bad
var i;
var items = [];
var block;
var name = 'Jder';
var age=26;

//good
var item = [];
var name = 'Jder';
var age = 26;
var i;
var block;
```

* 在作用域顶部声明变量
```javascript
//bad
function verify(){
    test();
    var name = getName();
    if(name === 'Jder'){
        return true;
    }
    return name;
}

//good
function verify(){
    var name = getName();
    test();
    if(name === 'Jder'){
        return true;
    }
    return name;
}
```

块
---
* `if/else`、`while`、`for`作用域内必须用大括号`{}`包裹
```javascript
//bad
if(condition)
    return true;
    
//good
if(condition){
    return true
}
```
* 如果通过`if/elseif/else`使用多行代码块，必须把`elseif/else`放在关闭括号`}`的同一行
```javascript
//bad
if(condition){
    //TODO
}
else{
    //TODO
}

//good
if(condition){
    //TODO
}else if(condition){
    //TODO
}else{
    //TODO
}
```

* 使用`/** ... */`作为多行注释
```javascript
// bad
// make() return a new element
// based on the passed in tag name
// 
// @param {String} tag
// @return {Element} element
function make(tag) {
    //TODO
    return element;
}

//good
/**
* make() return a new element
* based on the passed in tag name
* 
* @param {String} tag
* @return {Element} element
*/
function make(tag) {
    //TODO
    return element;
}
```

* 使用`//`作为单行注释。在注释对象上面另起一行使用单行注释
```javascript
//bad
var active =true; //is current tab

//good
//is current tab
var active = true;
```
* 在代码块内，若是荡漾注释，需要在注释前插入一个空行
```javascript
//bad
function getType(){
    console.log('fetching type...');
    // set the default type to 'no type'
    var type = this.type || 'no type';
    return type;
}
//good
function getType(){
    console.log('fetching type...');
    
    // set the default type to 'no type'
    var type = this.type || 'no type';
    return type;
}
```

空格
---


* 在大括号`{`前放一个空格

```javascript
//bad
function test(){
    console.log("test");
}
//good
function test() {
    console.log("test");
}
```

* 在控制语句`if/else`、`while`、`for`等控制语句的`(`前放一个空格
```javascript
//bad
if(condition) {
    return true;
}
//good
if (condition) {
    return true;
}
```

* 在函数调用及声明中，不在函数的参数列表前加空格
```javascript
//bad
function sayHello () {
    console.log("Hello");
}

//good
function sayHello() {
    console.log("Hello");
}
```

* 使用空格将运算符隔开
```javascript
//bad
var x=y+5;

//good
var x = y +5;
```

* 在文件末尾插入一个空行
```javascript
//bad
(function(){
    // do something...
})();
```
```javascript
//good
(function(){
    // do something...
});

```



*在块末尾和新语句前插入空行
```javascript
//bad
function test1() {
    // do something...
}
function test2() {
    // do something...
}

//good
function test1() {
    // do something
}

function test2() {
    // do something
}
```

* 禁止使用末尾逗号`,`

```javascript
//bad
var person = {
    name: 'Jder',
    age: 26,
}

//good
var person = {
    name: 'Jder',
    age: 26
}
```

分号
---
* 使用分号
```javascript
//bad
(function(){
    // do something...
})()

//good
(function(){
    // do something...
})();
```

命名规则
---
* 避免使用单字母进行命名。命名应该具有描述性
```javascript
//bad 
function q() {
    // do something...
}

//good
function query() {
    // do something...
}
```

* 使用驼峰式命名对象、函数和实例
```javascript
//bad
var this_is_my_object = {};

//good
var thisIsMyObject = {};
```

* 声明自定义对象（类）时首字母应大写
```javascript
//bad
var user = function(options) {
    this.name = options.name;
}

//good
var User = function(options) {
    this.name = options.name;
}
```

* 使用`that`来保存`this`引用
```javascript
//bad
function init() {
    var self = this;
    function inner() {
        console.log(self);
    }
}

//good
function init() {
    var that = this;
    function inner() {
        console.log(that);
    }
}
```

* 文件名应该与类名相同
```javascript
//bad
// filename radio.js
var CheckBox = function() {
    
}

//good
//filename CheckBox.js
var CheckBox = function() {
    
}
```

对象自定义方法
---
* 创建自定义对象时，应给对象分配原型方法，而不是覆盖原型
```javascript
var User = function(options) {
    this.name = options.name;
    this.age = options.age;
    
}

//bad
User.prototype = {
    getName: function() {
        return this.name;
    },
    getAge: function() {
        return this.age;
    }
}

//good
User.prototype.getName = function() {
    return this.name;
}

User.getAge = function() {
    return this.age;
}
```

模块
---
* 模块的定义应该以`+`开头
> 确保某些不好的模块忘记包含最后的分号，使得其在代码合并后不会产生错误
* 在模块顶部添加`'use strict';`声明
```javascript
+(function($){
    'use strict';
    
    // do something...
})(jQuery)
```

jQuery
---
* 使用`$`作为存储jQuery对象的变量名前缀
```javascript
//bad
var dom = $('.container');

//good
var $dom=$('.container');
```

*缓存jQuery对象
```javascript
//bad
function setNavBar() {
    $('.nav-bar').show();
    $('.nav-bar').css({
        'position':'fixed',
        'border':'1px solid #333333'
    });
}

//good
function setNavBar() {
    var $navBar=$('nav-bar');
    $navBar.show();
    $navBar.css({
        'position':'fixed',
        'border':'1px solid #333333'
    });
}
```