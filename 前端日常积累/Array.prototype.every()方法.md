## Array.every()
> every() 方法用来测试数组中的 `所有元素` 是否通过了被提供的函数测试, 返回一个 Boolean 值.  

- 空数组测试, 任何情况下都返回 `true` .
- `every()` 方法只会在一个有值的索引上被引用, 不会被那些删除或未被赋值的索引上引用.
- `every()` 方法在遍历数组时, 从第 `0` 个开始, 遇到第一个能返回 `false` 的 `callback` 函数, 就会停止后续的 `callback` . 

### 语法
```js
array.every(function (currentValue, index, arr), thisArg)
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
- 返回值
  - 返回 `Boolean` 值.  
  - 数组中所有元素满足条件就返回 `true`, 否则返回 `false`.
- JavaScript 版本:
  - 1.6

### 描述  
`every()` 为数组中的每一个元素都执行一次 `callback` 函数, 直到所有 `callback` 返回 `true` , 否则返回 `false`. `callback` 只会在一个有值的索引上被调用, 不会在那些被删除或从未被赋值的索引上引用.   

### 栗子
检测数组里是否所有值都 > 10
```js
var arr1 = [20, 13, 1, 5, 15]
function greaterThan10 (currentVal) {
  console.log(currentVal, '=> currentVal')
  return currentVal > 10
}
// 普通写法
console.log(arr1.every(greaterThan10))

// 使用箭头函数写法
console.log(arr1.every(n => n > 10))
```
打印结果:
> 20 "=> currentVal"  
13 "=> currentVal"  
1 "=> currentVal"  
false  

~ over ~
