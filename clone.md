# 浅拷贝和深拷贝

## 浅拷贝

数据分为基本数据类型(String, Number, Boolean, Null, Undefined，Symbol)和对象数据类型

基本数据类型存储在栈(stack)中，对象数据类型存放在堆内存，栈(stack)中存放的是指针，该指针指向堆中该实体的起始地址。

```javascript
let a = {
    name: 'joe',
    age: 13
}
let b = a
b.name = 'tom'
console.log(a.name === 'tom')   // true
```
`只是复制对象的指针地址称为浅拷贝`。

## 深拷贝

### 利用字符串转换完成拷贝

缺点：不能拷贝正则、日期和函数

```javascript
let a = {
    name: 'joe',
    age: 33,
    child:{
        name: 'licy',
        age: 4
    }
}
let b = JSON.parse(JSON.stringify(a));
b.child.name = 'lucy'
console.log(a.child.name);    // licy
```

### Object.assign()

缺定：只能深拷贝一层。

```javascript
let a = {
    name: 'joe',
    age: 33,
    child:{
        name: 'licy',
        age: 4
    }
}
let b = Object.assign({}, a);
b.child.name = 'lucy'
console.log(a.child.name);     // lucy
```

### ES6对象扩展运算符（…）

缺定： 只能深拷贝一层

```javascript
let a = {
    name: 'joe',
    age: 33,
    child:{
        name: 'licy',
        age: 4
    }
}
let b = {...a};
b.child.name = 'lucy'
console.log(a.child.name);     // lucy
```

### 手写函数实现深拷贝

```javascript
function deepClone(source) {
  if (!source && typeof source !== 'object') {
    throw new Error('error arguments', 'deepClone')
  }
  const targetObj = source.constructor === Array ? [] : {}
  Object.keys(source).forEach(keys => {
    if (source[keys] && typeof source[keys] === 'object') {
      targetObj[keys] = deepClone(source[keys])
    } else {
      targetObj[keys] = source[keys]
    }
  })        
  return targetObj
}
let a = {
    name: 'joe',
    age: 33,
    child:{
        name: 'licy',
        age: 4
    }
}
let b = deepClone(a);
b.child.name = 'lucy'
console.log(a.child.name);     // licy
```

### 函数库lodash(兼容性处理更好)
```javascript
const _ = require('lodash');         // 需要npm下载lodash依赖包
let a = {
    name: 'joe',
    age: 33,
    child:{
        name: 'licy',
        age: 4
    }
}
let b = _.cloneDeep(a);
b.child.name = 'lucy'
console.log(a.child.name);     // licy
```







