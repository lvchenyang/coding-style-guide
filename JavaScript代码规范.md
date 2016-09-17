 [1. 代码风格](#codeStyle)<br/>
 [1.1 编码](#encoding)<br/> 
 [1.2 结构](#structure) <br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.1 缩进](#indent)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.2 空格](#space)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.3 换行](#wrap)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.2.4 语句](#statement)<br/>
[1.3 命名](#naming)<br/>
[1.4 注释](#notes)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.4.1 单行注释](#singleNotes)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[1.4.2 多行注释](#multiNotes)<br/>


[2. 语言特性](#language)<br/>
[2.1 变量](#variable)<br/>
[2.2 控制语句](#contralStatment)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.2.1 if/else/where/for](#ifElse)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.2.2 switch](#switch)<br/>
[2.3 字符串](#string)<br/>
[2.4 数组](#array)<br/>
[2.5 函数](#function)<br/>
[2.6 面向对象](#object)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.6.1 对象的声明与创建](#defineObject)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.6.2 属性](#attributes)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[2.6.3 原型琏方法](#method)<br/>

[2.7 模块](#modular)<br/>


[3.jQuery](#jQuery)<br/>



# <a id="codeStyle">1. 代码风格</a>
## <a id="encoding">1.1 编码</a>
JavaScript文件的编码建议使用UTF-8格式。





### <a id="structure">1.2 结构</a>


#### <a id="indent">1.2.1 缩进</a>
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


#### <a id="space">1.2.2 空格</a>
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

* `,`和`;`前不应该有空格
```javascript
//bad
var name = 'Jder' ;

//good
var name = 'Jder';
````

* `{}`、`[]`、'()'内紧贴括号部分不应该有空格
```javascript
//bad
test( options, args );
var obj = { };
var arr = [ ];

//good
test(options,args);
var obj = {};
var arr = [];
```

* 参数列表内或者语句内的英文标点符号后应有一个空格占位符
```javascript
//bad
test(options,args);

//good
test(options, args);
````
* 行尾不能有多余的空格
```javascript
//bad
var name = 'Jder';·····

//good
var name = 'Jder';
````





#### <a id="wrap">1.2.3 换行</a>
* 每个独立语句结束后必须换行
```javascript
//bad
var name = 'Jder'; var age = 26;

//good
var name = 'Jder';
var age = 26;
```
* 在文件末尾插入一个换行符
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
* 在块末尾和新语句前插入换行
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

#### <a id="statement">1.2.4 语句</a>
* 复杂条件逻辑语句，将每个条件独立一行，逻辑判断语句放在行首，且注意缩进
```javascript
//bad
if(user.isAuthenticated() && user.isInRole() && user.hasAuthority('add-admin') || user.hasAuthority('delete-admin')){
    
}

//good
if(user.isAuthenticated()
    && user.isInRole()
    && user.hasAuthority('add-admin')
    || user.hasAuthority('delete-admin')){
    
}
```

* 拼接HTML字符串必须用`+`号进行拼接，且HTML片段与HTML缩进一致（第一行用空字符串占位）
```javascript
//bad
var html = '<article><h1>This is title</h1><p>This is content</p><footer>This is footer</footer></article>'

//good
var html = ''
         + '<article>'
         +     '<h1>This is title</h1>'
         +     '<p>This is content</p>'
         +     '<footer>This is footer</footer>'
         + '</article>'

//good
var html = [
    '<article>',
        '<h1>This is title</h1>',
        '<p>This is content</p>',
        '<footer>This is footer</footer>',
    '</article>'
];
html = html.join('');
```

* 函数的参数太多(大于等于5个)，则一行一个参数，并将结束的`)`独立一行
```javascript
//bad
foo(arg1, arg2, arg3, arg4, arg5)

//good
foo(
     arg1,
     arg2,
     arg3,
     arg4,
     arg5
);
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


### <a id="naming">1.3 命名</a>
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

//bad
var n = 'Jder';

//good
var name = 'Jder';
```

* 使用驼峰式命名对象、函数和实例
```javascript
//bad
var this_is_my_object = {};

//good
var thisIsMyObject = {};
```

* 使用function声明自定义对象（类）时首字母应大写
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

* 常量命名所有字母大写，并单词之间用下划线`_`分割
```javascript
//bad
var const_obj = {};

//bad
var constObj = {};

//bad
var CONSTOBJ = {};

//good
var CONST_OBJ = {};
```

### <a id="notes">1.4 注释</a>
#### <a id="singleNotes">1.4.1 单行注释</a>
* 使用`//`作为单行注释。在注释对象上面另起一行使用单行注释
```javascript
//bad
var active =true; //is current tab

//good
//is current tab
var active = true;
```
* 在代码块内，若是单行注释，需要在注释前插入一个空行
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
#### <a id="multiNotes">1.4.2 多行注释</a>
* <a id="multiNotes-1">使用文档化注释`/** ... */`作为多行注释</a>
```javascript
// bad
// make() return a new element
// based on the passed in tag name
// 
// @param {String} tag
// @return {Element} element
function make(tag) {
    // {code block}
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
    // do something...
    return element;
}
```

* 文件、类、类属性、全局变量、函数/方法、事件必须使用文档化注释进行注释

>see [文档化多行注释](@multiNotes-1)


# <a id="language">2 语言特性</a>

### <a id="variable">2.1 变量</a>
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

### <a id="controlStatment">2.2 控制语句</a>
#### <a id="ifElse">2.2.1 if/else</a>
* `if/else`、`while`、`for`作用域内必须用大括号`{}`包裹
```javascript
//bad
if(condition)
    // do something...
    
//good
if(condition){
    // do something...
}
```
* 如果通过`if/elseif/else`使用多行代码块，必须把`elseif/else`放在关闭括号`}`的同一行
```javascript
//bad
if(condition){
    // do something...
}
else{
    // do something...
}

//good
if(condition){
    // do something...
}else if(condition){
    // do something...
}else{
    // do something...
}
```
#### <a id="switch">2.2.2 switch</a>
// TODO: 定义switch编码规范

### <a id="string">2.3 字符串</a>
* 使用单引号`''`包裹字符串
```javascript
//bad
var name = "Tom"
//good
var name = 'Tom'
```
* 超过100个字符的字符串应该使用连接符写成多行

### <a id="array">2.4 数组</a>
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

### <a id="function">2.5 函数</a>
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

### <a id="object">2.6 面向对象</a>
#### <a id="defineObject">2.6.1 对象的声明与创建</a>
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
#### <a id="attributes">2.6.2 属性<a>
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
#### <a id="method">2.6.3 原型琏方法</a>
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

### <a id="modular">2.7 模块</a>
* 模块的定义应该以`+`开头
> 确保某些不好的模块忘记包含最后的分号，使得其在代码合并后不会产生错误
* 在模块顶部添加`'use strict';`声明
```javascript
+(function($){
    'use strict';
    
    // do something...
})(jQuery)
```

# <a id="jQuery">3 jQuery</a>
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