HTML5

1.播放第一个识别的视频

```HTML
<!--视频标签-->
<video src="movie.ogg" controls="controls">
  <source src="/i/movie.ogg" type="video/ogg">
  <source src="/i/movie.mp4" type="video/mp4">
</video>
```

2.播放第一个识别的音频

```html
<audio controls="controls">
  <source src="song.ogg" type="audio/ogg">
  <source src="song.mp3" type="audio/mpeg">
Your browser does not support the audio tag.
</audio>
```

3.**canvas 元素用于在网页上绘制图形。**

```html
<canvas id="myCanvas" width="200" height="100"></canvas>
```

4.**HTML5 支持内联 SVG。**

```html
<!DOCTYPE html>
<html>
<body>

<svg xmlns="http://www.w3.org/2000/svg" version="1.1" height="190">
  <polygon points="100,10 40,180 190,60 10,60 160,180"
  style="fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;" />
</svg>

</body>
</html>
```

5.HTML5 Geolocation API 用于获得用户的地理位置

6.HTML5 提供了两种在客户端存储数据的新方法：

- localStorage - 没有时间限制的数据存储

  ```js
  // 创建
      localStorage.setItem("lastname", "Gates");
  // 访问
  	localStorage.getItem("lastname")
  ```

  

- sessionStorage - 针对一个 session 的数据存储

  ```js
  //创建
  sessionStorage.pagecount=1;
  //访问
  sessionStorage.pagecount
  ```

  

7.应用程序缓存

```html
<!DOCTYPE HTML>
<html manifest="demo.appcache">

<body>
The content of the document......
</body>

</html>
```

8.输入框

##### HTML5 新的 Input 类型

HTML5 拥有多个新的表单输入类型。这些新特性提供了更好的输入控制和验证。

本章全面介绍这些新的输入类型：

- email
- url
- number
- range
- Date pickers (date, month, week, time, datetime, datetime-local)
- search
- color

9.表单元素

```html
<form action="/example/html5/demo_form.asp" method="get">
Webpage: <input type="url" list="url_list" name="link" />
<datalist id="url_list">
	<option label="W3School" value="http://www.w3school.com.cn" />
	<option label="Google" value="http://www.google.com" />
	<option label="Microsoft" value="http://www.microsoft.com" />
</datalist>
<input type="submit" />
</form>
```



![image-20200304205026810](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304205026810.png)

10.autofocus 属性 自动获取焦点

11.autocomplete 属性规定 form 或 input 域应该拥有自动完成功能。

12.form 属性规定输入域所属的一个或多个表单。

```html
<form action="demo_form.asp" method="get" id="user_form">
First name:<input type="text" name="fname" />
<input type="submit" />
</form>
Last name: <input type="text" name="lname" form="user_form" />
```

13.输入框min、max 和 step (一次增加多少)属性

14.multiple 属性文件多选

15.novalidate 属性不验证

16.pattern 属性规定用于验证 input 域的模式（pattern）。正则验证

```html
Country code: <input type="text" name="country_code"
pattern="[A-z]{3}" title="Three letter country code" />
```

17.placeholder 属性提供一种提示（hint），描述输入域所期待的值。输入框默认提示信息

18.required 属性规定必须在提交之前填写输入域（不能为空）。必填属性

### css3

**1.过渡  transition  : all 0 ease 0**

| *[transition-property](https://www.runoob.com/cssref/css3-pr-transition-property.html)* | 指定CSS属性的name，transition效果          |
| ------------------------------------------------------------ | ------------------------------------------ |
| *[transition-duration](https://www.runoob.com/cssref/css3-pr-transition-duration.html)* | transition效果需要指定多少秒或毫秒才能完成 |
| *[transition-timing-function](https://www.runoob.com/cssref/css3-pr-transition-timing-function.html)* | 指定transition效果的转速曲线               |
| *[transition-delay](https://www.runoob.com/cssref/css3-pr-transition-delay.html)* | 定义transition效果开始的时候               |

**2.动画  animation** mymove 5s infinite

@keyframes mymove
{
	from {left:0px;}
	to {left:200px;}
}

| *[animation-name](https://www.runoob.com/cssref/css3-pr-animation-name.html)* | 指定要绑定到选择器的关键帧的名称                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| *[animation-duration](https://www.runoob.com/cssref/css3-pr-animation-duration.html)* | 动画指定需要多少秒或毫秒完成                                 |
| *[animation-timing-function](https://www.runoob.com/cssref/css3-pr-animation-timing-function.html)* | 设置动画将如何完成一个周期                                   |
| *[animation-delay](https://www.runoob.com/cssref/css3-pr-animation-delay.html)* | 设置动画在启动前的延迟间隔。                                 |
| *[animation-iteration-count](https://www.runoob.com/cssref/css3-pr-animation-iteration-count.html)* | 定义动画的播放次数。                                         |
| *[animation-direction](https://www.runoob.com/cssref/css3-pr-animation-direction.html)* | 指定是否应该轮流反向播放动画。                               |
| [animation-fill-mode](https://www.runoob.com/cssref/css3-pr-animation-fill-mode.html) | 规定当动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式。 |
| *[animation-play-state](https://www.runoob.com/cssref/css3-pr-animation-play-state.html)* | 指定动画是否正在运行或已暂停。                               |
| initial                                                      | 设置属性为其默认值。 [阅读关于 *initial*的介绍。](https://www.runoob.com/cssref/css-initial.html) |
| inherit                                                      | 从父元素继承属性。 [阅读关于 *initinherital*的介绍。](https://www.runoob.com/cssref/css-inherit.html) |

3.**形状转换**  transform

rotate(30deg) [角度] ;  translate(30px,30px);  scale(.8) [放大缩小];    skew(10deg,10deg);    rotateX(180deg);   rotateY(180deg);    rotate3d(10,10,10,90deg);

4.**阴影**  box-shadow:10px 10px 5px [3px] #888888 [inset];  

| *h-shadow* | 必需的。水平阴影的位置。允许负值                             |
| ---------- | ------------------------------------------------------------ |
| *v-shadow* | 必需的。垂直阴影的位置。允许负值                             |
| *blur*     | 可选。模糊距离                                               |
| *spread*   | 可选。阴影的大小                                             |
| *color*    | 可选。阴影的颜色。在[CSS颜色值](https://www.runoob.com/cssref/css_colors_legal.aspx)寻找颜色值的完整列表 |
| inset      | 可选。从外层的阴影（开始时）改变阴影内侧阴影                 |

5.**边框**  border-image: url(border.png) 30 round(平铺，stretch不平铺);

6.**背景** background-clip 制定背景绘制

7.**.Filter**（滤镜）

8.**弹性布局** [F](https://links.jianshu.com/go?to=https%3A%2F%2Flink.juejin.im%2F%3Ftarget%3Dhttp%3A%2F%2Fwww.ruanyifeng.com%2Fblog%2F2015%2F07%2Fflex-grammar.html)lex

9.**栅格布局** grid

10.**盒模型定义**  box-sizing:border-box的时候，边框和padding包含在元素的宽高之内！              box-sizing:content-box的时候，边框和padding不包含在元素的宽高之内！

11.**媒体查询**

### ES6

1.不一样的变量声明：const和let

2.ES6反引号`(${})直接搞定；

3.箭头函数()=>{} (=>this指向.谁定义指向谁)(function谁调用指向谁)

4.函数的参数默认值

5.扩展运算符

```JS
function testFunc(...args) {
   console.log(args);  // ['aa', 'bb', 'cc']
   console.log(args.length); // 3
}
 // 调用函数
 testFunc('aa', 'bb', 'cc');

let arrs1 = ['aa', 'bb'];
let arrs2 = ['cc', 'dd'];
// 合并数组
let arrs = [...arrs1, ...arrs2];
// 析构数组
let param1, param2;
[param1, ...param2] = arrs1;

console.log(param1); // aa
console.log(param2); // ['bb']
//把类数组对象转换成数组 
var toArray = [...arguments];
//数组的深度拷贝
var arr1 = [1, 2];
var arr2 = [...arr1];
arr1.push(3);
console.log(arr1); // [1, 2, 3]
console.log(arr2); // [1, 2]
```

6.变量的解构

```js
let {a,b}=o;
ler [a,b]=o;
```

7.二进制和八进制字面量

```js
let oValue = 0o10;
console.log(oValue); // 8
 
let bValue = 0b10; // 二进制使用 `0b` 或者 `0B`
console.log(bValue); // 2
```

8.ES6 允许在对象中使用 super 方法：

```js
var parent = {
  foo() {
    console.log("Hello from the Parent");
  }
}
 
var child = {
  foo() {
    super.foo();
    console.log("Hello from the Child");
  }
}
 
Object.setPrototypeOf(child, parent);
child.foo(); // Hello from the Parent
             // Hello from the Child
```

9.for...of 和 for...in

10.ES6中的类

ES6 中支持 class 语法，不过，ES6的class不是新的对象继承模型，它只是原型链的语法糖表现形式。

```
class Student {
  constructor() {
    console.log("I'm a student.");
  }
 
  study() {
    console.log('study!');
  }
 
  static read() {
    console.log("Reading Now.");
  }
}
  //类中的继承和超集：
console.log(typeof Student); // function
let stu = new Student(); // "I'm a student."
stu.study(); // "study!"
stu.read(); // "Reading Now."

class Phone {
  constructor() {
    console.log("I'm a phone.");
  }
}

class MI extends Phone {
  constructor() {
    super();
    console.log("I'm a phone designed by xiaomi");
  }
}
 
let mi8 = new MI();
```

