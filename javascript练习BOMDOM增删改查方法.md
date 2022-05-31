```c
//欢迎加我VX进群交流
vx账号：-Sep07
```
# 一、Dom
dom的全称是Document Object Model，翻译为：文档对象模型。
在Js中我们通过Dom来对HTML文档进行操作，通过学习Dom便能随心所欲的操作Web页面
D：文档，一个html就是一个文档
O：对象，表示将网页中的每一个部分都转换成一个一个对象从而进行操作
M：模型，用来表示对象之间的关系，方便获取到对象
# 二、节点
## 1.Node（节点）
Node即为节点，是指构成网页的最基本的组成部分，网页中的每一个部分都可以被称作为一个`节点`，但是节点的具体类型则各不相同，网页中有如下几种常用的节点：
>文档节点：Html
>元素节点：每一个<>标签
>属性节点：每一个元素的属性
>文本节点：标签中所包含的文本内容
>
>节点的属性：如元素节点中包含的`value` `type`等属性

## 2.dom查询：
浏览默认提供文档节点对象，该对象是`window`的属性，我们可以直接使用，通过文档节点能够获取到对象，如：

```javascript
document.getElementById("btn");
//该方法便是通过文档节点来获取到ID为"btn"的对象。
document.getElementsByTagName("标签名");
//该方法可以通过标签名来获取到一组对象

//class属性值查询元素的方法
var box1 = document.getElementsByClassName("box1");
//该种查询方法只支持IE9以上的浏览器
```
案例演示：

```xml
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script>
		window.onload=function(){
			//获取body标签
			var body =document.getElementsByTagName("body")[0];//获取到的是一个类数组，需要添加[0]取出来
			/*
			可以用下列方法获取body标签，更为简便
				var body = document.body;
			*/
			console.log(body);
			//document.documentElement保存的是HTML的根标签
			//document.all 查询到页面中的所有的标签
			//class属性值查询元素的方法
			var box1 = document.getElementsByClassName("box1"){
				//只支持IE9以上的浏览器
			};	
		}
		</script>
	</head>
	
<body>

</body>
</html>
```

---

# 三、DOM的其它方法：
常用的dom方法有如下几种:
qppendChild( )
添加子节点到指定节点

remoreChild( )
删除子节点

replaceChild( )
替换子节点

createElement( )
创界元素节点

createTextNode( )
创建文本节点
# 四、querySelector选择器

## 1.案例演示
在进行增删查的演示之前先学会使用querySlelctor选择器
通过使用该选择器我们可以直接使用`CSS选择器`的方法来查找到一个元素，如：`var box1 = document.querySelector("#id1  div");`
案例演示：

```xml
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script>
		window.onload=function(){
			
			// querySelector();
			//可以根据css选择器来查询一个元素节点对象
			document.querySelector(".box1 div");
			//该方法只会返回一个元素，但如果符合条件的元素有多个则只会返回第一个
		
			var all = document.querySelectorAll("div");
			//该方法和quertSelector不同之处在于会将符合条件的"多个"元素封装到一个“数组”中返回。
			//遍历所有的div
			for(var i = 0; i<all.length; i++){
				console.log(all[i]);
			}
		};
		</script>
	</head>
	<body>
		<div class="box1">
			<div>
			</div>
		</div>
	</body>
</html>
```


# 四、dom的增删查演示：

```xml
<html>
	<head>
		<meta charset="utf-8">
		<title></title>
		<script>
//首先绑定单击响应函数
		function myClick(idStr,fun){
			var btn = document.getElementById(idStr);
			btn.onclick = fun;
		};
		window.onload=function(){
		
//需求一、创建一个广州节点添加到city下面
			myClick("btn01",function(){
			//1.创建广州节点
			var li = document.createElement("li");
			//创建广州的文本节点
			var gzText = document.createTextNode("广州");
					//向父节点li中添加子节点gztext
					li.appendChild(gzText);
				
			//2.将节点添加到city下
			var city = document.getElementById("city");
			city.appendChild(li);
			});
			//1.创建广州节点
			var li = document.createElement("li");
			//创建广州的文本节点
			var gzText = document.createTextNode("广州");
				//向父节点li中添加子节点gztext
					li.appendChild(gzText);
					
					
					
//需求二、将广州节点插入到#bj前面
			myClick("btn02",function(){
			var li = document.createElement("li");
				//创建广州的文本节点
			var gzText = document.createTextNode("广州");
					//向父节点li中添加子节点gztext
					li.appendChild(gzText);
				
				//获取id为bj的节点
				var bj = document.getElementById("bj");
				var city = document.getElementById("city");
				city.insertBefore(li,bj);
			});
			
			
//需求三、使用广州节点替换#bj节点
		myClick("btn03",function(){
			var li = document.createElement("li");
			//创建广州的文本节点
			var gzText = document.createTextNode("广州");
			//向父节点li中添加子节点gztext
			li.appendChild(gzText);		
			var bj = document.getElementById("bj");
			var city = document.getElementById("city");
			//父节点.replaceChild(新节点,旧节点)使用指定参数替换
			city.replaceChild(li,bj);
				
			});
			
			
//需求四、删除bj节点
		myClick("btn04",function(){
			var bj = document.querySelector("#bj");
			var city = document.querySelector("#city");
			city.removeChild(bj);
			})；

//需求五、修改bj内的HTML代码	
		myClick("btn06",function(){
			var bj = document.querySelector("#bj");
			bj.innerHTML = "昌平";
			});
			
			/*################
			此外还可以利用如下方法向city中添加广州
			但该方法虽然简单，但对city中代码的影响太大
			所以一般两种方法结合使用
			*/
			myClick("btn07",function(){
				var city = document.querySelector("#city");
				//city.innerHTML = ("<li>广州2</li>");
				//city.innerHTML += ("<li>广州2</li>");
				var li = document.createElement("li");
				li.innerHTML = "广州2";
				city.appendChild(li);
			});
			
			
		};
		</script>
</head>
	<body>
		<div id="total">
			<div class="inner">
				<p>
					你喜欢那个城市
				</p>
				<ul id="city">
					<li id="bj">北京</li>
					<li>上海</li>
					<li>东京</li>
					<li>首尔</li>
				</ul>
			</div>
		</div>
		<div id="btnList">
			<div><button id="btn01">创建一个广州节点添加到#city下</button></div>
			<div><button id="btn02">将广州节点插入到#bj前面</button></div>
			<div><button id="btn03">使用广州节点替换#bj节点</button></div>
			<div><button id="btn04">删除#bj节点</button></div>
			<div><button id="btn05">读取city内的html代码</button></div>
			<div><button id="btn06">设置#bj内的html代码</button></div>
			<div><button id="btn07">方式二创建一个广州节点添加到#city下</button></div>
		</div>	
	</body>
</html>
```
```c
//欢迎加我VX进群交流
vx账号：-Sep07
```