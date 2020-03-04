#  vue-cli 3.x 之后适配手机端

**先安装 npm i postcss-pxtorem  --save -dev**

**在根目录创建文件夹postcss.config.js**

```js
module.exports = {
  plugins: {
    'autoprefixer': {
      browsers: ['Android >= 4.0', 'iOS >= 7']
    },
    'postcss-pxtorem': {
      rootValue: 16,//结果为：设计稿元素尺寸/16，比如元素宽320px,最终页面会换算成 20rem
      propList: ['*']
    }
  }
}
```

或者 在根目录创建文件夹vue.config.js(如果没有的话)

```js
module.exports = {

 lintOnSave: true,

  css: {

   loaderOptions: {

    postcss: {

     plugins: [

      require("postcss-pxtorem")({

       //这里是配置项，详见官方文档

       rootValue: 16, // 换算的基数

       selectorBlackList: [], // 忽略转换正则匹配项

       propList: ["*"]

      })

     ]

    }

   }

  }

};
```

**操作到这里移动端自动适配了吗，当然不能，目前只是将px单位转换成rem,移动端适配还差最后一步,初接触rem理解起来有点懵，后来发现了一个好理解的方法，下面来分享一下。**

**我们现在可以把CSS中的px单位换成rem单位来进行测试。因为html根元素的字体大小是16px，那么换成rem单位，直接除以16就好。**

**明白了REM的原理后，我们就可以使用这个特点来进行适应布局了，这也是现在比较主流的移动端web适配方案。**

**src目录下，新建 libs/rem.js 输入如下代码**



```js
// 设置 rem 函数
function setRem () {

    // 320 默认大小16px; 320px = 20rem ;每个元素px基础上/16
    let htmlWidth = document.documentElement.clientWidth || document.body.clientWidth;
//得到html的Dom元素
    let htmlDom = document.getElementsByTagName('html')[0];
//设置根元素字体大小
    htmlDom.style.fontSize= htmlWidth/20 + 'px';
}
// 初始化
setRem();
// 改变窗口大小时重新设置 rem
window.onresize = function () {
    setRem()
}
```

在main.js中引入rem.js

```js
import './libs/rem.js';
```