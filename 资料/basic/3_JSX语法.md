## 一、语法规则

​    jsx语法规则：

​      1.定义虚拟DOM时，不要写引号。

​      2.标签中混入JS表达式时要用{}。

​      3.样式的类名指定不要用class，要用***className***。

​      4.内联样式，要用**style={{key:value}}**的形式去写。

​      5.只有**一个根标签**

​      6.标签必须**闭合**

​      7.标签首字母

​        (1).若小写字母开头，则将该标签转为html中同名元素，若html中无该标签对应的同名元素，则报错。

​        (2).若大写字母开头，react就去渲染对应的组件，若组件没有定义，则报错。

​		**组件大写字母开头**

## 二、代码

```javascript
		//1.创建虚拟DOM
		const VDOM = (
			<div>
				<h2 className="title" id={myId.toLowerCase()}>
					<span style={{color:'white',fontSize:'29px'}}>{myData.toLowerCase()}</span>
				</h2>
				<h2 className="title" id={myId.toUpperCase()}>
					<span style={{color:'white',fontSize:'29px'}}>{myData.toLowerCase()}</span>
				</h2>
				<input type="text"/>
			</div>
		)
```

## 三、练习

   *一定注意区分：【js语句(代码)】与【js表达式】*

-    **表达式**：一个表达式会产生一个值，可以放在任何一个需要值的地方

​        *下面这些都是表达式：*

​          *(1). a*

​          *(2). a+b*

​          *(3). demo(1)*

​          *(4). arr.map()* 

​          *(5). function test () {}*

-   **语句(代码)**：

​        *下面这些都是语句(代码)：*

​          *(1).if(){}*

​          *(2).for(){}*

​          *(3).switch(){case:xxxx}*

```javascript
		//模拟一些数据
		const data = ['Angular','React','Vue']
		//1.创建虚拟DOM
		const VDOM = (
			<div>
				<h1>前端js框架列表</h1>
				<ul>
					{
						data.map((item,index)=>{
							return <li key={index}>{item}</li>
						})
					}
				</ul>
			</div>
		)
		//2.渲染虚拟DOM到页面
		ReactDOM.render(VDOM,document.getElementById('test'))
```

注意：react不能遍历对象