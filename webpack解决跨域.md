```js
module.exports={
    devServer:{
        proxy:{//代理
           '/api':{
               target:"http://127.0.0.1:3000",
               pathRewrite:{
                   '/api':""
               }
           }
        }
    }
}
```

npm install -S webpack-dev-middleware