```js
Object.defineProperty(o, "b", {
    get : function(){
        return bValue;
    },
    set : function(newValue){
        bValue = newValue;
    },
    enumerable : true,
    configurable : true
});//定义对象属性


Object.preventExtensions() //对象扩展
Object.isExtensible() //对象是否可扩展
Object.seal() //对象配置
Object.isSealed() //一个对象是否可配置
Object.freeze() //一个对象
Object.Frozen() //一个对象是否被冻结
Object.creat() //可以指定原型对象和属性，返回一个新的对象
Object.getPrototypeOf() //获取对的的Prototype对象
Object.setPrototypeOf //设置一个指定的对象的原型
Object.is() //判断是否相等
Object.assign() //用于对象的合并 浅拷贝
Object.keys() //方法，返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（ enumerable ）属性的键名数组。
Object.values()//方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（ enumerable ）属性的键值数组。
Object.entries() //方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（ enumerable ）属性的键值对数组。
JSON.stringify() //只串行化对象自身的可枚举的属性。
//call()方法与 apply()方法和bind()方法的作用和区别
//这三种方法共同的作用是实现修改this的指向
//apply()和 call()这两个方法的用途都是在特定的作用域中调用函数，实际上等于设置函数体内 this 对象的值

```

