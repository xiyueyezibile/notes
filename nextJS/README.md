# NextJS

## 初始化next

```
npx create-next-app 名字
```

启动nextjs服务器

```
npm run dev
```

## 初始nextJS

nextJS里面pages下面一个js，jsx，ts，tsx就是一个页面

## Link and a

nextjs中link标签用于跳转页面。

与a标签形式基本一致，使用前需要引入

```
import Link from "next/link"
<Link href="/posts/first-post">
        111
      </Link>
```

## 修改HTML中Head的标签

通过<Head></head>

```
import Head from "next/head"
<Head>
	<title>111</title>
</Head>
```

## 全局作用的css

把css引入在pages目录下_app.js里面

## 动态路由

可以通过useRouter拿到路由

创建[id].js

```
const router = useRouter()
router.query.id
```

## 加载脚本和图片

通过引入Script和Image在public下进行加载

![image-20230129164455416](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230129164455416.png)

![image-20230129164517946](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230129164517946.png)

![image-20230129164535688](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230129164535688.png)

## 获取数据

![image-20230131112751624](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230131112751624.png)

![image-20230131112735552](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230131112735552.png)

![image-20230131112921532](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230131112921532.png)

![image-20230131113737600](C:\Users\潘麒麟\AppData\Roaming\Typora\typora-user-images\image-20230131113737600.png)
