## 一、JSX 创建虚拟DOM

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>1_使用jsx创建虚拟DOM</title>
</head>
<body>
	<!-- 准备好一个“容器” -->
	<div id="test"></div>

	<!-- 引入react核心库 -->
	<script type="text/javascript" src="../js/react.development.js"></script>
	<!-- 引入react-dom，用于支持react操作DOM -->
	<script type="text/javascript" src="../js/react-dom.development.js"></script>
	<!-- 引入babel，用于将jsx转为js -->
	<script type="text/javascript" src="../js/babel.min.js"></script>

	<script type="text/babel" > /* 此处一定要写babel */
		//1.创建虚拟DOM
		const VDOM = (  /* 此处一定不要写引号，因为不是字符串 */
			<h1 id="title">
				<span>Hello,React</span>
			</h1>
		)
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))
	</script>
</body>
</html>
```

## 二、JS 创建虚拟DOM

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>2_使用js创建虚拟DOM</title>
</head>
<body>
	<!-- 准备好一个“容器” -->
	<div id="test"></div>

	<!-- 引入react核心库 -->
	<script type="text/javascript" src="../js/react.development.js"></script>
	<!-- 引入react-dom，用于支持react操作DOM -->
	<script type="text/javascript" src="../js/react-dom.development.js"></script>

	<script type="text/javascript" > 
		//1.创建虚拟DOM  React.createElement
		const VDOM = React.createElement('h1',{id:'title'},React.createElement('span',{},'Hello,React'))
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))
	</script>
</body>
</html>
```

## 三、区别

JSX 为了更快捷创建虚拟DOM

(可以认为是js创建虚拟DOM的语法糖)

![1699406254569](C:\Users\13000\AppData\Roaming\Typora\typora-user-images\1699406254569.png)

浏览器真正运行，会利用babel转换成js：

![1699406322573](C:\Users\13000\AppData\Roaming\Typora\typora-user-images\1699406322573.png)

## 四、虚拟DOM和真实DOM的区别

​    **关于虚拟DOM：**

​     *1.本质是Object类型的对象（一般对象）*

​     *2.虚拟DOM比较“轻”，真实DOM比较“重”，因为虚拟DOM是React内部在用，无需真实DOM上那么多的属性。*

真实DOM 属性很多：

![1699406547800](C:\Users\13000\AppData\Roaming\Typora\typora-user-images\1699406547800.png)

虚拟DOM属性相对少：

![1699406582287](C:\Users\13000\AppData\Roaming\Typora\typora-user-images\1699406582287.png)

​     *3.虚拟DOM最终会被React转化为真实DOM，呈现在页面上。*

