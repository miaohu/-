## jQuery 整体架构-核心功能函数揭秘
### jQuery源码解析
- `jQuery` 无 `new` 构建实例
- 共享原型设计
- `extend` 源码解析

## 准备
- 空 `demo.html` 文件
- 空 `jQuery-1.0.1.js` 文件
- `jQuery-2.1.1.js` 源码

## 无 new 化构建实例
- $ 就是 `jQuery` 的别称
- `$()` 就是 `jQuery` 的实例对象

## 开始
`demo.html` 文件引入
```html
<script src="./jQuery-1.0.1.js"></script>
```
`jQuery-1.0.1.js` 文件, 创建代码架子
```js
(function(root){
    var jQuery = function () {
        
    }
    // 给 window 对象上扩展一个 $ 的属性, 让它拿到 jQuery 构造函数的引用
    root.$ = root.jQuery = jQuery;
})(this);
```
思考: 该如何在调用 `jQuery()` 时去创建实例?  
```js
console.log($())
```
在页面上访问 `$()` 时, 目的是创建 `jQuery` 实例. `$` 指向 `jQuery` 这个构造函数, `$()` 方法实际是调用这个构造函数.



我们会很容易想到, 通过 `new` 创建 `jQuery` 实例:
```js
var jQuery = function () {
  return new jQuery();
}
```
上面的做法看似可以, 但其实很不合理, 从设计上就很有问题.
当通过 new 创建 jQuery 实例, 会做两步操作:
- 去创建一个 `Object` 对象
- 去调用自身的构造函数

这样就进入了死循环, 那么 `jQuery` 是如何来解决这个问题的呢?

先来了解一下 `jQuery` 的共享原型设计. 先上代码:
```js
  jQuery.fn = jQuery.prototype = {
    init: function () {

    },
    css: function () {

    }
  }
```
共享原型对象
```
jQuery.fn.init.prototype = jQuery.fn;
```
> 在 jQuery 定义一个
