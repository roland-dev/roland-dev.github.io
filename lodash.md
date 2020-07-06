# Lodash 学习

## lodash 思维

lodash并不只是提供了一些数据处理的基础方法，同时还方便了我们以 Functional Programming 的思路来进行数据处理。

1. `referential transparency` 相同参数，每次调用，返回的结果都是一样的。
2. `lack-of-side-effects` 无side effects，也就是不会改变“外面的世界”
3. `Immutable` 所有的方法都不会改变传入参数的原始对象，只会返回一个新的对象。
4. `Auto-curried` 所有的方法都是柯理化的
5. `Iteratee-first` 处理过程（函数）作为第一个参数传入
6. `Data-last` 处理对象作为最后的参数传入

## lodash 使用

### 按需加载(减少代码量)

lodash是可以按需加载的，如果我只需要 map，那么我可以 import map from 'lodash/fp/map'，它就只会引入 map 相关的代码。

### 对象深拷贝(_.cloneDeep())
```javascript
var objects = [{ 'a': 1 }, { 'b': 2 }];
 
var deep = _.cloneDeep(objects);
console.log(deep[0] === objects[0]);
// => false
```

### 流式调用函数(_.flow())
```javascript
function square(n) {
  return n * n;
}
 
var addSquare = _.flow([_.add, square]);
addSquare(1, 2);
// => 9
```
