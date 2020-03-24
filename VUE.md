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

## 5.中央事件总线

```js
// 新建一个 Bus.vue文件,new 一个 vue 实例导出
export default new Vue({
    name: 'bus',
    data () {
        return {
            // code
        }
    }
})

// 可以理解为这是一个传话人员
// 新建一个组件 A
<tempalte>
    <button @click="sendMessage"向组件 B 发送数据</button>
</tempalte>
<script>
import Bus from 'Bus.vue'
    export default {
        name: 'componentA',
        data () {
            return {
                msg: 'the message is from componentA'
            }
        },
        methods: {
            sendMessage () {
                // 假设知道组件 B 有个方法叫做 inceptMessage(接收数据的方法)
                // 组件 A对组件 B 说 我要通过 Bus 这个传话员给你传话了,你先告诉我
                // 这么理解,当组件 A 通过 Bus 传话员去触发inceptMessage这个方法的时候,组件 B 是可以感应到组件 A 调用了这个方法的
                Bus.$emit('inceptMessage', this.msg)
                // Bus 通过触发组件 B 的inceptMessage方法将 msg 发送过去了,这个时候组件 B 还不知道组件 A 给它发送了一条数据
            }
        }
    }
</script>
// 新建一个组件 B
<tempalte>
    // 显示组件 A 传过来的数据
    <h1>{{ fromComponentAMsg }}</h1>
</tempalte>
<script>
import Bus from 'Bus.vue'
    export default {
        name: 'componentB',
        data () {
            return {
                fromComponentAMsg: ''
            }
        },
        methods: {

        },
        mounted () {
            // 这个时候组件 B 知道组件 A 给它传了一条数据过来了,于是赶紧叫 Bus 这个传话员把数据告诉它
            // bus 就告诉组件 B, 组件 A 那边通过inceptMessage传过来一条数据叫 msg
            Bus.$on('inceptMessage',(msg) => {
                this.fromComponentAMsg = msg
            })
        }
    }
</script>
```

## 6 . 组件前进刷新,后退不刷新

```js
export default {
    name: 'xxx',
    data () {
        //...
    },
    deactivated () {
     this.$destroy()
   },
   methods: {
    // ...
    }
}
//$destroy完全销毁一个实例。清理它与其它实例的连接，解绑它的全部指令及事件监听器。
```

