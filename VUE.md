## 1.vue编程式导航的原理

##### 注意：一定要区分 `this.$route` 和 `this.$router` 这两对象

`this.$route` 是路由参数的对象，`this.$route.params.id`、`this.$route.query` 都属于它

`this.$router` 是路由导航对象，使用它可以方便的使用JS代码，实现前进、后退、跳转到新的URL

```JS
this.$router 常用方式：
// 命名的路由
router.push({ name: 'user', params: { userId: '123' }})
// 带查询参数，变成 /register?plan=private
router.push({ path: 'register', query: { plan: 'private' }})
```

router.push()原理：

这个方法，会向history栈添加一个新记录，之前<router-link>,在内部也是调用了此方法，用户点击浏览器后退按钮时，会返回到之前的url。

## 2.计算属性和侦听属性的区别

计算属性适合用在模板渲染中，某个值是依赖了其它的响应式对象甚至是计算属性计算而来；而侦听属性适用于观测某个值的变化去完成一段复杂的业务逻辑。

​	**计算属性不能执行异步任务，计算属性必须同步执行**

- watch：监测的是属性值， 只要属性值发生变化，其都会触发执行回调函数来执行一系列操作。
- computed：监测的是依赖值，依赖值不变的情况下其会直接读取缓存进行复用，变化的情况下才会重新计算

- computed能做的，watch都能做，反之则不行
- 能用computed的尽量用computed

## 3.vue如果要进行dom操作有什么要注意的地方

**DOM操作不要放在munted之前，vue中munted之前页面dom还没有渲染完毕，在munted之前获取不到vue中的dom**

```js
<input @change="fileChange($event)" ref='file' type="file" style="display: none"/>
//this.$refs.file
```

## 4.vuex中的Mutations原理	

commit：状态改变提交操作方法。对`mutation`进行提交，是唯一能执行`mutation`的方法