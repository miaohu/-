## Array.includes()
> includes() 检测一个数组里是否包含某个指定的值, 如果包含返回 `true` 否则返回 `false`.  

- 要检索的值是的在数组里某个元素的一部分, 返回 `false`. (参考 `Demo1`)  
- `includes()` 方法的第二个参数 `大于等于` 数组的长度, 返回 `false`.  
- `includes()` 方法的第二个参数为 `负值` 按 `升序` 从 `array.length + fromIndex` 处的索引开始查找.
- `includes()` 方法的第二个参数, 计算出的索引值 < 0, 那么整个数组都会被搜索.  

### 语法
```js
array.includes(findElement, fromIndex)
```

##### 参数
- findElement
  - 必须。要检索的值
- fromIndex
  - 可选。从该索引处查找.
  - 允许为负值。若为负值, 按 `升序` 从 `array.length + fromIndex` 的索引开始查找.  

##### 细节
- 返回值:
  - 返回一个 `Boolean` 值. 如果数组里包含某个指定的值, 返回 `true` 否则返回 `false`.  
- JavaScript 版本:
  - ECMAScript 6



### 栗子
##### Demo1
检测数组中是否含有某个 `字符串`
```js
// 字符串
var nameArr = ['Luna', 'bai', 'Jennifer'];
// 数组中某个元素 返回 true
console.log(nameArr.includes('Luna'), '=> Luna') 
// 数组某元素的一部分 返回 false
console.log(nameArr.includes('Jenn'), '=> Jenn') 
```
打印结果:
> true "=> Luna"  
false "=> Jenn"  

##### Demo2
检测数组中是否含有某个 `数字`  
```js
var numArr = [1, 3, 5, 7];
// 数组中某个数字 返回 true
console.log(numArr.includes(5), '=> 5') 
// fromIndex < 0 索引处从 nameArr.length+(-1) 处开始
// 计算出来的索引值 > 0
console.log(numArr.includes(3, -1), '=> fromIndex: -1')
// fromIndex < 0 索引处从 nameArr.length+(-100) 处开始
// 计算出来的索引值 < 0, 整个数组都会被搜索
console.log(numArr.includes(3, -100), '=> fromIndex: -100')
// fromIndex 大于数组长度 false
console.log(numArr.includes(3, 4), '=> fromIndex: 4') 
// fromIndex 大于数组长度 false
console.log(numArr.includes(3, 5), '=> fromIndex: 5') 
```
打印结果:
> true "=> 5"  
false "=> fromIndex: -1"  
true "=> fromIndex: -100"  
false "=> fromIndex: 4"  
false "=> fromIndex: 5"  

##### Demo3  
作为通用方法的 `includes()` 
> `includes()` 方法有意设计为通用方法, 它不要求 `this` 值是数组对象, 所以它可以被用于其他类型的对象(比如类数组对象).  

在函数 `arguments` 对象上调用 `includes()` 方法.
```js
(function(){
  console.log([].includes.call(arguments, 'a'), '=> a');
  console.log([].includes.call(arguments, 'd'), '=> d');
})('a', 'b', 'c');
```
打印结果:
> true "=> a"  
false "=> d"  

~ over ~