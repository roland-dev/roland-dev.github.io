# 原型和原型链

## 原型

### 定义

`原型（prototype）`是在开发早期表現对象的属性和方法的模型。
`原型模式` 用原型实例指向创建对象的类，使用于创建新的对象的类的共享原型的属性与方法。

### 原型继承

谈到原型，不得不说的就是继承，JavaScript只有一种类型就是对象。其他类型都是继承于Object对象。
每个实例对象（ object ）都有一个私有属性（称之为 __proto__ ）指向它的构造函数的原型对象（prototype ）。该原型对象也有一个自己的原型对象( __proto__ ) ，层层向上直到一个对象的原型对象为 null。根据定义，null 没有原型，并作为这个原型链中的最后一个环节。

```javascript
let Person = function(name){
    this.name = name
    this.showMe = function(){      // 这里不能写箭头函数
        alert(this.name)
    }   
}
```

Person是一个对象，它有一个prototype的原型属性（因为所有的对象都一prototype原型！）prototype属性有自己的prototype对象，而pototype对象肯定也有自己的constuct属性，construct属性有自己的constuctor对象，神奇的事情要发生了，这最后一个constructor对象就是我们构造出来的function函数本身！

