1. 运行 初始化项目 npm init -y
2. 在项目更目录创建src源文件目录和dist产品目录
3. 在src目录下创一个index.html
4. 使用cnpm （npm i cnpm -g）安装webpack， cnpm i webpack  webpack-cli -D
5.  webpack 4.x中，又一个很大的特性，就是约定大于配置，约定，默认的打包入口路径是 src => index.js

打包指令很多（npx webpack，./node_modules/.bin/webpack ,添加脚本dev 以运行）

webpack能处理js/json资源，不能处理css/img等其他资源，

生产环境和开发环境将ES6模块化编译成浏览器能识别的模块化~

生产环境比开发环境多一个压缩js代码。

webpack.config.js webpack的配置文件（指示webpack干那些活（当你运行webpack指令是，会加载里面的配置））

所有构造工具都是基于nodejs平台运行的~模块化默认采用commonjs。

webpack 自身提供了一些参数来优化编译任务，以下简单列出了一些参数：

| 参数                    | 描述                   |
| ----------------------- | ---------------------- |
| --config                | 指定配置文件           |
| --watch, -w             | 监听变动并自动打包     |
| -p                      | 压缩混淆脚本           |
| --progress              | 显示进度条             |
| --display-reasons       | 显示添加打包模块的原因 |
| --display-error-details | 出错时错误的详情       |

> 提示：想了解webpack更多参数，可在终端输入 `./node_modules/.bin/webpack -h` 查看

这里以监听为例，执行编译的时候带上 -w 参数，如下所示：

```
$ ./node_modules/.bin/webpack --config ./build/webpack.dev.config.js  -w
```

当你对文件做了任何修改都会进行自动编译，如果你想要取消监听状态，可使用快捷键：`CTR/CMD+C`

可以发现，如果执行编译任务，特别是在参数比较多的情况，是比较麻烦的，我们可以在 npm 的 ”package.json“ 文件中进行添加一个脚本指令的字段，如下所示：

```json
"scripts": {
  "build":"./node_modules/.bin/webpack --progress --display-modules --display-reasons --display-error-details --watch"
},
```

在 ”package.json“ 文件中配置添加完脚本配置之后，我们可直接通过如下令执行打包任务，如下所示:npm run build

```js
/*
loader:1.下载 2.使用（配置loader）
plugins:1.下载 2.引入 3.使用
*/
const {resolve} = require('path');
//下载npm i html-webpack-plugin -D 引入
const HtmlWebpackPlugin = require("html-webpack-plugin");
modeule.exports={
	//webpack配置项
    //入口起点
    entry:"./src/index.js",
    //输入
    output:{
        //输出文件名
        filename:'built.js',
        //输出路径
        //__dirname nodejs 的变量，代表当前文件的目录结对路径
        path:resolve(__dirname,"built")
    },
    //loader的配置
    module:{
        rules:[
            //详细loader配置
            
            //为什么要加这个处理css样式的loader
            //因为webpack不能解析打包css文件，所以需要loader将css文件处理转化为js文件进行打包
            {
                //在index.js 文件里 import './index.css'
                //（也就是匹配需要处理的文件）匹配那些文件
                test:/\.css$/,//(处理匹配.css结尾的文件)
                //处理这些css文件需要那些loader
                //要使用多个loader处理的时候就用use，只用到一个的时候就用loader
                use:[
                    //use数组中loader的执行顺序：从右到左，从上到下，依次执行
                    //创建style标签，将js中的的样式资源插入进去，添到head中生效
                    'style-loader',//需要下载 npm i style-loader -D
                    //将css文件变成commonjs模块加载到js中,也就是将css用js字符串的形式写在了js文件里
                    'css-loader'//需要下载 npm i css-loader -D
                ]
            },
            //为什么要加这个处理less样式的loader
            //因为webpack不能解析打包less文件，所以需要loader将less文件处理转化为css文件,在将这个css文件处理转化为js文件进行打包
            {
                //在index.js 文件里 import './index.less'
                //（也就是匹配需要处理的文件）匹配那些文件
                test:/\.less$/, //(处理匹配.less结尾的文件)
                //处理这些less文件需要那些loader
                use:[
                    //use数组中loader的执行顺序：从右到左，从上到下，依次执行
                    //创建style标签，将js中的的样式资源插入进去，添到head中生效
                    'style-loader',//需要下载 npm i style-loader -D
                    //将css文件变成commonjs模块加载到js中,也就是将css用js字符串的形式写在了js文件里
                    'css-loader',//需要下载 npm i css-loader -D
                    {
                        //npm i postcss-loader autoprefixer -D
                        //自动添加前缀（autoprefixer）指定兼容版本需在 “package.json”中的“browserslist”字段中配置即可
                    //  "browserslist": [
                    	// "last 2 version"
                      //]
                        loader: "postcss-loader",
                        options: {
                            ident: "postcss",
                            plugins: [
                                require("autoprefixer")
                            ]
                        }
                    }
                    'less-loader'//需要下载 npm i less-loader less -D
                ]
            },
            {
                //问题：在html直接加图片地址用图片 默认处理不了html中img图片的
                //处理图片资源
                test:/\.(jpg|png|gif)$/
                //要使用多个loader处理的时候就用use，只用到一个的时候就用loader
                //下载 npm i url-loader file-loader -D
                loader:'url-loader',
                //处理图片的配置项(处理图片的时候约束处理)
                options:{
                	//图片大小小于8kb，就会被base64处理
                	//优点：减少请求数量（减轻服务器压力）
                	//缺点：图片体积会更大(文件请求速度更慢)
                	limit:8 * 1024,
                	//问题：因为url-loader默认使用es6模块化解析的，而html-loader引入图片是commonjs，解释时会报错
                	//解决:关闭url-loader的es6模块化，使用commonjs解析
                	esModule:false,
                	//给图片进行重命名
                	//[hash:10]去图片的hash前10位
                	//[ext]去文件原来的扩展名
                	name:"[name]-[hash:5].[ext]",
                	// 输出路径
            		otputPath: "static/images/",
            	}
            },
            {
            	//处理html文件的img图片（负责引入img，从而能被url-loader进步处理打包）
            	test:/\.html$/,
            	loader:'html-loader'//npm i html-loader -D
            },
    		//打包其他资源（除了css/js/html/图片资源以外的资源
    		{	//排除css|js|html资源文件
    			exclude:/\.(css|js|html)$/
				loaer:'file-loader',//file-loader基于url-loader的可以换成url-loader
    			options:{
    				name:'[hash:10].[ext]'
				}
			},
            // 编译es语法
            {
                test: /\.js$/,
				//下载：npm i -D babel-loader @babel/core @babel/preset-env
                use: {
                    loader: "babel-loader",
                    options: {
                        presets: ["@babel/preset-env"]
                    }
                }
			}
        ]
    }
    //plugins的配置
    plugins:[
    	//详细pulgins的配置
    	//html-webpack-plugin
    	//功能：默认会创建一个空的Html，自动引入打包输出的所有资源(js/css)
    	//需求：需要有结构的Html文件
    	new HtmlWebpackPlugin({
    		//引入一个html文件，并自动引入打包输出的所有资源(js/css)
    		template:'./src/index.html'
	})
    ],
    //模式
    mode:'development',//开发模式
    //mode:'production',//生产模式
    //开发服务器devServer:用来自动化（自动编译，自动打开浏览器，自动属性浏览器~~）
    //特点：只会在内存中编译打包，不会有任何输出
    //启动devServer指令为：npx webpack-dev-server    
    //下载 npm i webpack-dev-server -D
    devServer:{
        //运行构建后打目录
        contentBase:resolve(__dirname,'build'),
        //启动gzip压缩
        compress:true,
        host: "127.0.0.1",
        //端口号
        port：3000,
        //默认打开浏览器
        open:true
    }
}
```



