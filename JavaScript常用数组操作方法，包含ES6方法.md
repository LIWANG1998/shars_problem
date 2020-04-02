## 一、concat()

concat()方法用来链接两个或者多个数组，该方法不会改变原数组，会返回一个新数组可接收

```js
let arrayTwo = ["1", "2"];
let arrayOne = ["liwang", "xiem", "ergou"];
let a = arrayTwo.concat(arrayOne);
console.log(a, arrayTwo, arrayOne);
```

## 二、join()

join()方法用于将数组转化给字符串，可以指定分隔符连接成字符串，默认链接符为逗号，有返回值可接收

```js
let arrayOne = ["liwang", "xiem", "ergou"];
let stringA = arrayOne.join("-");
console.log(stringA);
```

## 三、push(),unshift()

push()方法是向数组尾部添加元素，可一次添加多个元素，会改变原数组，返回的是数组长度。

unshift()方法是向数组头部添加元素，可一次添加多个元素，会改变原数组，返回的是数组长度。

```js
let arrayTwo = ["1", "2"];
let b = arrayTwo.push("3", "4");
console.log(arrayTwo);
```

## 四、pop(),shift()

pop()方法是删除数组最后一个元素，返回被删除的元素，会改变原数组

shift()方法是删除数组头一个元素，返回被删除的元素，会改变原数组

```js
let arrayTwo = ["1", "2"];
console.log(arrayTwo.pop());
console.log(arrayTwo);
```

## 五、slice()

slice()数组的截取，两个删除，开始下标和结束下表，结束下标不包括进去,返回一个新数组可接收，不会改变原数组

```js
let a = [1, 2, 3, 4, 5];
console.log(a.slice(1,3))
```

## 六、splice()

splice()数组的删除，替换，添加, 改变原数组，有返回值，返回的是删除的元素数组集合

splice（开始的下边，要删除的个数，要添加的元素，要添加的元素，……）

```js
let a = [1, 2, 3, 4, 5
console.log(a.splice(1, 1, 9, 8)) // [2];
console.log(a);
```

## 七、substring(),substr()

substring()和substr()都是字符串的截取

不同点：

substring(开始下表（不算在截取内），结束下表（算在截取内）)

substr(开始下表（不算在截取内），截取的个数)

## 八、sort() 数组排序

sort() 用与数组的排序  Unicode code 排序，默认升序 ，会改变原数组，有返回值，可接收,

可传入一个函数，比较大小返回

```
let a = [100, 21, 3, 4, 56, 1];
let b = a.sort((l, n) => l - n);
console.log(b, a);
```

## 九、reverse() 倒序

reverse()会改变原数组，返回的是颠倒后的数组

```js
let b = [100, 21, 3, 4, 56, 1];
b.reverse();
console.log(b);
```

## 十、indexOf 和 lastIndexOf

indexOf( 需要找的元素，指定元素出现的下表)是从数组前面查找第一个匹配元素的下标

lastindexOf(需要找的元素，指定元素出现的下表) 是从数组后面开始查找第一个匹配的元素下标

返回值为匹配的下标，没匹配上就返回-1

```js
var a = [2, 9, 9];
a.indexOf(2); // 0
a.indexOf(7); // -1
```

## 十一、every()

every(func) 有返回值，为true和，false，

每一项都运行给定的函数，有一个为false就返回

```js
let a = [100, 21, 3, 3, 56, 1];
let b = a.every((item, index, arr) => {
  console.log(item, index, arr);
  return item > 0;
});
console.log(b);
```

## 十二、some()

some()对数组的每一项都运行给定的函数，任意一项都返回 ture,则返回 true

```js
let arr = [
  { id: 1, name: "liwang1", age: 15 },
  { id: 3, name: "liwang2", age: 14 },
  { id: 4, name: "liwang2", age: 16 },
  { id: 2, name: "liwang4", age: 18 },
  { id: 1, name: "liwang5", age: 18 }
];
let b = arr.some((item, index, arr) => {
  return item.name == "liwang1";
});
console.log(b);
```

## 十三、filter()

filter()对数组的每一项都运行给定的函数，返回 结果为 ture 的项组成的数组(就是过滤掉不匹配的元素，让匹配的元素)

```js
let arr = [
  { id: 1, name: "liwang1", age: 15 },
  { id: 3, name: "liwang2", age: 14 },
  { id: 4, name: "liwang2", age: 16 },
  { id: 2, name: "liwang4", age: 18 },
  { id: 1, name: "liwang5", age: 18 }
];
let b = arr.filter((item, index, arr) => {
  return item.age >= 16;
});
console.log(b);
```

## 十四、map()

map()对数组的每一项都运行给定的函数，返回每次函数调用的结果组成一个新数组，不改变原数组

```js
let arr = [
  { id: 1, name: "liwang1", age: 15 },
  { id: 3, name: "liwang2", age: 14 },
  { id: 4, name: "liwang2", age: 16 },
  { id: 2, name: "liwang4", age: 18 },
  { id: 1, name: "liwang5", age: 18 }
];
let b = arr.map((item, index, arr) => {
  return { ...item, age: item.age * 2 };
});
console.log(b);
console.log(arr);
```

## ES6新增新操作数组的方法

## 1、find()

find()传入一个回调函数，找到数组中符合当前搜索规则的第一个元素，返回它，并且终止搜索。(找符合回调函数的 值 )

```js
let a = [100, "21", 3, 3, "56", 1];
console.log(
  a.find((item, index) => {
    return typeof item === "number";
  })
);
// 100
```

## 2、findIndex()

findIndex()传入一个回调函数，找到数组中符合当前搜索规则的第一个元素，返回它的下标，终止搜索。(找符合回调函数条件的 下标）

```js
let a = [100, "21", 3, 3, "56", 1];
console.log(
  a.findIndex((item, index) => {
    return typeof item === "number";
  })
);
// 0
```

## 3、fill()

fill(换的元素，开始下标，结束下标（不包含在内）)  挨个挨个替换，改变原数组。

```js
let a = [100, "21", 3, 3, "56", 1];
a.fill("你不是我", 0, 3);
console.log(a);
//[ '你不是我', '你不是我', '你不是我', 3, '56', 1 ]
```

## 4、from()

Array.from(zhi):将类似数组的对象（array-like object）和可遍历（iterable）的对象转为真正的数组

```js
let name = "liwang";
let a = Array.from(name);
console.log(a);
//[ 'l', 'i', 'w', 'a', 'n', 'g' ]
```

## 5.includes()

includes()匹配数组中存不存在元素，存在返回true，不存在返回false

```js
var a = [1, 2, 3];
console.log(a.includes(2));
console.log(a.includes(4));
```

