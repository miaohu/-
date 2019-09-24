## Array.some()
> some() 方法用来测试数组中是否有元素通过了被提供的函数测试, 返回一个 Boolean 值.  

- 空数组测试, 任何情况下都返回 `false` .
- `some()` 方法只会在一个有值的索引上被引用, 不会被那些删除或未被赋值的索引上引用.
- `some()` 方法在遍历数组时, 从第 `0` 个开始, 遇到第一个能返回 `true` 的 `callback` 函数, 就会停止后续的 `callback` .  

### 语法
```js
array.some(function (currentValue, index, arr), thisArg)
```

##### 参数
- `function (currentValue, index, arr)`  
  `必须` 数组中的每个元素都会执行这个函数.
  - `currentValue`  
    `必须` 当前元素的值.
  - `index`  
    `可选` 当前元素的索引值.
  - `arr`  
    `可选` 当前被遍历的数组.
- `thisArg`
  - `可选` 执行 `callback` 时使用的 `this` 值.
  - 如果省略了 `thisArg`, `this` 的值为 `undefined`.

##### 细节
- 返回值: 
  - 返回 `Boolean` 值.  
  - 数组中有一项满足条件就返回 `true`, 否则返回 `false`.
- JavaScript 版本:
  - 1.6

### 描述  
`some()` 为数组中的每一个元素都执行一次 `callback` 函数, 直到一个 `callback` 返回 `true` , 否则返回 `false`. `callback` 只会在一个有值的索引上被调用, 不会在那些被删除或从未被赋值的索引上引用.  

### 栗子
##### Demo1
```js
var arr = [1, 3, 5] // 返回 false
var arr = [1, 2, 3, 4, 5] // 返回 true
var even = function (element) {
  console.log(element, '=> element')  // 1 "=> element" 2 "=> element" true "=> even" 2 可以被整除, 返回 true, 后面的 3,4,5 都不会被 callback 执行.
  return element % 2 === 0
}
console.log(arr.some(even), '=> even')
```
打印结果:
> 1 "=> element"  
2 "=> element"  
true "=> even"  

##### Demo2
检测数组中是否有 >10 的元素.
```js
function compareNum(element, index, array) {
  // element: 当前正在处理的元素, index: 当前元素的下标, array: 被遍历的数组
  return element > 10
}
var arr1 = [3, 9, 8, 2, 6].some(compareNum)
var arr2 = [9, 15, 7, 10, 6].some(compareNum)
console.log(arr1, '=> arr1') // false "=> arr1"
console.log(arr2, '=> arr2') // true "=> arr2"
```
打印结果:
> false "=> arr1"  
true "=> arr2"  

##### Demo3
使用箭头函数测试数组元素的值
```js
var arr3 = [3, 9, 8, 2, 6].some(n => n > 10)
var arr4 = [9, 15, 7, 10, 6].some(n => n > 10)
console.log(arr3, '=> arr3')
console.log(arr4, '=> arr4')
```
打印结果:
> false "=> arr3"  
true "=> arr4"  

##### Demo4
判断数组元素中是否存在某个值 (模仿 includes() 方法, 若元素在数组中, 则回调函数返回值为 true)
```js
var nameList = ['Luna', 'Jenn', 'Lucky', 'Kitty']
function dealName (arr, val) {
  // 普通函数写法
  // return arr.some(function (name) {
  //   return val === name 
  // })
  // 箭头函数写法
  return arr.some(name => val === name)
}
var name1 = dealName(nameList, 'Luna')
var name2 = dealName(nameList, 'miaohu')
console.log(name1, '=> name1') // true
console.log(name2, '=> name2') // false
```
打印结果:
> true "=> name1"  
false "=> name2"  

##### Demo5
```js
var TRUTHY_VALUES = [true, 'true', 1];
function getBoolean(value) {
  'use strict';
  if (typeof value === 'string') { 
    value = value.toLowerCase().trim();
    console.log(value, '=> 转换小写')
  }
  return TRUTHY_VALUES.some(function(t) {
    console.log(t, '=> ttttttttt')
    return t === value;
  });
}
console.log(getBoolean('true'), '=> 打印结果');
```
打印结果:
> true => 转换小写
true "=> ttttttttt"  
true => ttttttttt  
true "=> 打印结果"  

~ over ~