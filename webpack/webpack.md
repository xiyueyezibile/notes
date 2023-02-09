# webpack

## 使用步骤

​	1.初始化项目 npm init -y

2. 安装依赖 webpack, webpack-cli

   ```
    npm i -D webpack webpack-cli
    -D 是开发依赖
   ```

   

3. 创建src目录，编写代码

4. 打包 npx webpack

## 配置文件

创建webpack.config.js

```
const path = require('path')
module.exports = {
  mode:"production", // 设置打包模式 production 生产模式 development 开发模式
  entry:"./hello.js", // 打包时的主文件 默认./src/index.js
  //可以传数组，设置多个入口文件，会打包成一个文件
  //可以传对象，会打包成多个文件，对象的属性为文件名
  output:{
    filename:"index.js", // 打包后的文件名
    //多文件filename:"[name].js",
    clean:true, // 是否事先清空打包目录
    path:path.resolve(__dirname,"dist"), //指定打包的目录，必须要绝对路径
  }, // 配置代码打包后的地址
  /* 使webpack可以处理其他类型的文件 */
  //处理css npm i css-loader -D
  //css-loader 只负责打包时把css转换为js，不会在页面时生效
  //npm i style-loader -D
  //style-loader 负责在页面中生效css样式
  module:{
    rules:[
      {
        test: /\.css$/i, //正则表达式，表示是处理.css结尾的文件
        //后面的先执行，顺序很重要
        use:["style-loader","css-loader"]
      },
      //图片webpack默认支持
      {
        test:/\.jpg$/i,
        type:"asset/resource" //图片这些资源类型的数据，通过指定type来处理
      }
    ]
  },
  plugins:[
  new HTMLPlugin({
  //title:"hello webpack"
  template:"./src/index.html" //设置模板html，以其为原型构建
  })
  ],
  devtool:"inline-source-map" //开发工具sourcemap
}
```

![image-20230209192820812](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230209192820812.png)

## 插件

为webpack扩展功能

html-webpack-plugin 打包时生成html页面

```
yarn add html-webpack-plugin -D
const HTMLPlugin = require("html-webpack-plugin")

```

## 开发服务器

```
yarn add -D webpack-dev-server
```

**启动服务器**

```
yarn webpack serve --open
```

