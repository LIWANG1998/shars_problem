# 如何将vue-cli3项目使用HBuilder打包移动端app

1.在更目录vue.config.js文件里面加publicPath: './',

```js
module.exports={
	publicPath: './',
}
```

2.路由方式换成hash模式

```js
const router = new VueRouter({
    mode: "hash",
    base: process.env.BASE_URL,
    routes
});

export default router;
```

3.运行npm run build 打包生成的dist文件

![image-20200304182654870](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304182654870.png)

4.开始使用 HBuiderX 打包

创建H5+app默认模板项目

![image-20200304182926172](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304182926172.png)基础配置appid

![image-20200304183031730](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304183031730.png)

然后在图标配置里面选择app图片，再自动生成所有图标，在unpackage下res的icons可以看到所有图标

![image-20200304183157037](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304183157037.png)

更具自己项目实际情况勾选填写，我用的都是默认的

![image-20200304184101570](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304184101570.png)

自己加上的代码

![image-20200304184429896](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304184429896.png)

发行打包App

![image-20200304184619784](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304184619784.png)

这里打包的安卓的，ios的需要申请证书。

![image-20200304184932121](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304184932121.png)

打包好了会出现下载地址

![image-20200304185049413](C:\Users\86152\AppData\Roaming\Typora\typora-user-images\image-20200304185049413.png)

这就已经打包好了！