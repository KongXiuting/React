# 一、Hello React

![img](https://cdn.nlark.com/yuque/0/2023/png/23171577/1699318461225-4c0da4fc-b0f7-4ae6-bbc3-8f25ffb8b879.png)

1. react.js：React核心库。
2. react-dom.js：提供操作DOM的React扩展库。
3. babel.min.js：解析JSX语法代码转为JS代码的库。

作用：①  es6 => es5 ； ②JSX => JS

注意：引入顺序要按上面的123来

## 代码：

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>hello_react</title>
</head>
<body>
	<!-- 一、准备好一个“容器” -->
	<div id="test"></div>

	<!-- 二、顺序有要求！！！ -->
	<!-- 1、引入react核心库 -->
	<script type="text/javascript" src="../js/react.development.js"></script>
	<!-- 2、引入react-dom，用于支持react操作DOM -->
	<script type="text/javascript" src="../js/react-dom.development.js"></script>
	<!-- 3、引入babel，用于将jsx转为js -->
	<script type="text/javascript" src="../js/babel.min.js"></script>

	<script type="text/babel" > /* 此处一定要写babel */
		//1.创建虚拟DOM
		const VDOM = <h1>Hello,React</h1> /* 此处一定不要写引号，因为不是字符串   JSX语法*/
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))
	</script>
</body>
</html>
```



## 运行效果：    

![1699405295310](C:\Users\13000\AppData\Roaming\Typora\typora-user-images\1699405295310.png)

*运行这个代码会有警告，暂时忽略，脚手架和开发者工具之后就没了*