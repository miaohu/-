## Object.keys()
> `Object.keys()` 返回一个数组, 数组成员是给定对象的自身可枚举属性的键名组成的数组.  

- 数组中属性名的排列顺序和使用 `for...in` 循环遍历该对象时返回的顺序一致.
- 如果对象的 `键-值` 都不可枚举(被遍历), 将返回由 `键` 组成的数组.  

### 语法
```js
Object.keys(obj)
```

##### 参数
- obj
  - 要返回其枚举自身属性的对象.

##### 细节
- 返回值: 
  - 给定对象的自身可枚举属性的键名组成的数组
- JavaScript 版本:
  - ECMAScript 6  

### 栗子
##### Demo1
从数组 colorArray 创建一个数组迭代对象, 该对象包含了 `数组元素的键`
```js
var colorArray = ['red', 'yellow', 'green', 'black']
console.log(Object.keys(colorArray), '=> colorArray')
```
打印结果:
> ["0", "1", "2", "3"] "=> colorArray"  

##### Demo2
从对象 colorObj 创建一个数组迭代对象, 该对象包含了 `对象元素的键`
```js
var colorObj = {0: 'red', 1: 'yellow', 2: 'green', 3: 'black'}
console.log(Object.keys(colorObj), '=> colorObj')
```
打印结果:
> ["0", "1", "2", "3"] "=> colorObj"

##### Demo3
对迭代出来的 `数组的键值` 排序
```js
var wordsObj = {20: 'a', 5: 'b', 16: 'c', 7: 'd'}
console.log(Object.keys(wordsObj), '=> wordsObj')
```
打印结果:
> ["5", "7", "16", "20"] "=> wordsObj"

##### Demo4
不可枚举的属性, 返回由键组成的数组
```js
var myObj = Object.create({}, {
  getFoo: {
    value: function () { return this.foo; }
  } 
});
myObj.foo = 1;
console.log(Object.keys(myObj), '=> myObj');
```
~ over ~