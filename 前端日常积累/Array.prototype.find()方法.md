## Array.find()
> find() 返回满足测试函数的第一个元素的值, 否则返回 `undefined`. 

- 空数组测试, 任何情况下都返回 `undefined` .
- `find()` 方法在遍历数组时, 从第 `0` 个开始, 遇到第一个能返回 符合条件 的 `callback` 函数, 就会停止后续的 `callback`, 并返回其值.  

### 语法
```js
array.find(function (currentValue, index, arr), thisArg)
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
  - 返回符合测试条件的第一个元素值, 如果没有返回 `undefined` 
- JavaScript 版本:
  - ECMAScript 6
 
### 描述  
`find()` 为数组中的每一个元素都执行一次 `callback` 函数, 直到一个 `callback` 返回 `true` , 然后立即返回这个值, 否则返回 `undefined`.

### 栗子
##### Demo1
返回数组里第一个 >10 的元素值
```js
var arr1 = [1, 12, 20, 15, 7]
var greaterThan10 = function (arr) {
  return arr.find(function (n) {
    console.log(n, '=> n')
    return n > 10
  })
}
// 普通写法
console.log(greaterThan10(arr1), '=> greaterThan10')

// 箭头函数写法
console.log(arr1.find(n => n > 10))
```
打印结果:
> 1 "=> n"  
12 "=> n"  
12 "=> greaterThan10"  

##### Demo2
用对象的属性, 查找数组里的对象
```js
var listInfo = [
  {name: 'Luna', age: '3'},
  {name: '小白', age: '5'},
  {name: '小花', age: '6'}
]
var findInfo = function (arr) {
  return arr.name === 'Luna'
}
console.log(listInfo.find(findInfo))
```
打印结果:
> {name: "Luna", age: "3"}  

稍微灵活一点的写法:
```js
var listInfo = [
  {name: 'Luna', age: '3'},
  {name: '小白', age: '5'},
  {name: '小花', age: '6'}
]
var findInfo = function (arr, nameStr) {
  // 普通写法
  // return arr.find(function (currObj) {
  //   return currObj.name === nameStr
  // })
  
  // 箭头函数写法(推荐)
  return arr.find(currObj => currObj.name === nameStr)
}
console.log(findInfo(listInfo, 'Luna'))
```
打印结果:
> {name: "Luna", age: "3"}  

~ over ~
