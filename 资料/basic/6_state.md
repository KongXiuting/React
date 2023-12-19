简单组件：无状态

复杂组件：有状态。

state：是组件示例对象的三大属性之一。

## 一、构造器constructor

```javascript
		//1.创建组件
		class Weather extends React.Component{
			
			//构造器调用几次？ ———— 1次
			constructor(props){
				console.log('constructor');
				super(props)
				//初始化状态
				this.state = {isHot:false,wind:'微风'}
				//解决changeWeather中this指向问题
				this.changeWeather = this.changeWeather.bind(this)
			}

			//render调用几次？ ———— 1+n次 1是初始化的那次 n是状态更新的次数
			render(){
				console.log('render');
				//读取状态
				const {isHot,wind} = this.state
				return <h1 onClick={this.changeWeather}>今天天气很{isHot ? '炎热' : '凉爽'}，{wind}</h1>
			}

			//changeWeather调用几次？ ———— 点几次调几次
			changeWeather(){
				//changeWeather放在哪里？ ———— Weather的原型对象上，供实例使用
				//由于changeWeather是作为onClick的回调，所以不是通过实例调用的，是直接调用
				//类中的方法默认开启了局部的严格模式，所以changeWeather中的this为undefined
				
				console.log('changeWeather');
				//获取原来的isHot值
				const isHot = this.state.isHot
				//严重注意：状态必须通过setState进行更新,且更新是一种合并，不是替换。
				this.setState({isHot:!isHot})
				console.log(this);

				//严重注意：状态(state)不可直接更改，下面这行就是直接更改！！！
				//this.state.isHot = !isHot //这是错误的写法
			}
		}
		//2.渲染组件到页面
		ReactDOM.render(<Weather/>,document.getElementById('test'))
```

onclick  => onClick

onblur  =>  onBlur

class     =>   className

注意：

onClick={this.changeWeather}



## 二、类中方法this指向

类中局部开启了严格模式。

onClick={this.changeWeather}，先赋值再调用，相当于直接调用



解决方法

（1）bind

this.changeWeather = this.changeWeather.bind(this);

**bind**:改变this指向，生成一个新函数

（2）箭头函数



## 三、state不能直接更改

要借助**setState**进行更改

更新是一种合并，不是替换



## 四、简写

**开发的时候写的**：

```javascript
		//1.创建组件
		class Weather extends React.Component{
			//初始化状态
			state = {isHot:false,wind:'微风'}

			render(){
				const {isHot,wind} = this.state
				return <h1 onClick={this.changeWeather}>今天天气很{isHot ? '炎热' : '凉爽'}，{wind}</h1>
			}

			//自定义方法————要用赋值语句的形式+箭头函数
			changeWeather = ()=>{
				const isHot = this.state.isHot
				this.setState({isHot:!isHot})
			}
		}
		//2.渲染组件到页面
		ReactDOM.render(<Weather/>,document.getElementById('test'))
```

类里面可以直接写赋值语句

```javascript
		class Car {
			constructor(name,price){
				this.name = name
				this.price = price
				// this.wheel = 4
			}
			//类中可以直接写赋值语句,如下代码的含义是：给Car的实例对象添加一个属性，名为a，值为1
			a = 1
			wheel = 4
			static demo = 100
		}
		const c1 = new Car('奔驰c63',199)
		console.log(c1);
		console.log(Car.demo);
```

箭头函数，没有自己的this；若使用了，就找外侧this。

类的自定义方法，都写成**赋值语句**加**箭头函数**。

## 五、总结

1、state是个对象，key-value组合；

2、组件被称为“状态机”，通过更新组件的state来更新对应页面显示。

