```c
//欢迎加我VX进群交流
vx账号：-Sep07
```
# 目录

有了第一阶段的基础知识后我们就开始进入到第二阶段的学习了。

---



@[TOC](文章目录)
---


# 一、对象的简介

对象`Object`，是一种复合类型，可以保存多个不同类型的属性。
对象又被分为如下几类：
- 1.内建对象
内建对象是ES标准中定义的对象，任何ES的实现中都可以使用。
- 2.宿主对象
宿主对象使用JS的运行环境提供的对象，再我们前端开发的学习中主要指的便是浏览器所提供的`BOM/DOM`、`console.log(),document.write()`等等。
- 3.自定义对象
自定义对象指的是由开发人员自行创建的对象。
## 1.创建对象
- 一、创建对象

```var obj = new Object();```
使用`new`关键字来调用的函数，如 `Object()`，叫做构造函数,是专门用来创建对象的函数。



- 二、像对象添加`属性`：
属性：是对象中保存的值，我们可以使用如下方法像对象添加属性
```javascript
var obj = new Object();
	obj.name = "zhaoxin";
	//对象名.属性名 = 属性值
```
- 三、读取对象中的属性：
```javascript
var obj = new Object();
	obj.name = "zhaoxin";

console.log(obj.name);
```
- 四、修改对象的属性值：
```javascript
var obj = new Object();
	obj.name = "zhaoxin";
	obj.name = "新值"
```
- 五、删除对象中的属性：
```javascript
var obj = new Object();
	obj.name = "zhaoxin";
	obj.name = "新值"

delete obj.name;
//可以使用该方法删除属性值，或属性。
```

- 六、属性名和属性值
属性的命名不强制要求标识符的规范，我们可以使用任意字符作为属性的名字，但特殊属性名的属性不能使用`.`来调用，只能使用`obj["123"]`这种方法来存取。（"123"是属性名）。使用改种方法来操作属性会更灵活。
属性值可以是**任意**的数据类型，甚至可以是对象。
- 七、in运算符
`in`运算符可以用来检查对象中是否有指定的属性，有则返回true，无则返回false
语法：
`console.log(test in obj);`
//检查test随想中是否含有obj属性。

## 2.内存结构图
![在这里插入图片描述](https://img-blog.csdnimg.cn/4fadf270961f4910a1437902d46ae14a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAVHJpbGxpb24tc3Rhcg==,size_20,color_FFFFFF,t_70,g_se,x_16#pic_center)



## 3.对象字面量
我们可以通过使用对象字面量的方式在创建对象时直接去指定对象的属性。
**语法：**
```javascript
var boj{
	name : "zhaoxin",
	age  : 24,
	}
	//使用名值对来制定对象的属性
```
# 二、函数
函数也是一个对象，但是相比起普通的对象，函数可以封装完整的某些功能。封装到函数中的代码并不会立即执行，只有在调用的函数的时候才会执行。
函数的创建方法：
```javascript
var fun = new Function();
//()中可以用字符串的形式传递封装的功能代码给构造函数
```
但该方法一般在开发中很少使用，**而一般在开发中创建函数的方法有如下三种：**
```javascript
//第一种
function fun ("形参"){
	//函数体
};
//第二种

var fun1 = function("形参"){
	//函数体
};

//第三种（匿名函数）
function(){
	函数体
};
```
## 1. 函数的参数

```javascript
function sum(a,b){
	console.log(a+b);
};
sum(1,2);
//我们可以在调用函数的时候传入实参
```
我们可以在调用函数的时候传入实参，但是在调用函数的时候，解释器并不会检查实参的数据类型与数量，如果这时候我们传入多余的实参则会被系统忽略。而传入的实参数量**小于**形参的数量，则会返回`undefind`。
## 2.函数的返回值
我们在定义一个函数的时候可以为函数指定一个返回值，具体的用法是在函数体执行完毕后，使用关键字`return` 在return后跟上要返回的数据。
**示例：**
```javascript
function sum(a,b,c){
	var d = a+b+c;
		return d;
	}
var result = sum(1,2,3);
//调用函数，传递实参，并得到返回值
//将得到的返回值传递给变量result接收
```
注意：返回值可以是任意的数据类型，当然也包括对象/函数，如果return后面没有跟上语句，则用于**`结束代码`**。
## 3.立即执行函数
用`(  )`将一个匿名函数括起来，再加一个`( )`便可以调用函数并立即执行。*立即执行函数往往只会执行一次。
```javascript
(function("形参"){
	//函数体；
})("实参");
```
# 三、方法
对象`Object`的属性可以是任何的数据类型，也包括函数；
一般可以将匿名函数作为对象的属性，这样我们便可以通过调用对象属性的方式来调用函数，我们称这种调用形式叫做调用**方法**。
>**对象存属性、函数存功能**
>**对象的属性如果是函数，那么便叫做对象的方法**
>
>创建一个对象的方法：
```javascript
var obj = new Object();
	obj.name = "zhaoxin";
	obj.age  = 24;
	obj.fun = function(){
		console.log(name,age);
		};
//调用对象的方法：
	obj.fun();
```

## 1. 枚举对象中的属性（取出对象中的所有属性）
可以使用for循环来取出对象当中的所有属性，语法：
```javascript
var obj = new Object();
	obj.name = "zhaoxin";
	obj.age = 24;
	obj.gender = "man";
	
	for(var i in obj){
		console.log("属性名"+n);
		console.log("属性值"+obj[i]);
	}//使用此方式可以取出对象中的所有属性名与属性值
```
## 2.作用域
（变量的作用范围）：
### 1、全局作用域：
- 直接编写在`<script></script>`标签中的代码，在页面打开的时候被创建，在页面关闭时销毁。
- 全局作用域中有一个全局对象`window`，该对象由浏览器创建，代表的是浏览器的窗口，可以直接使用。在全局作用域当中，创建的所有变量都会被作为`window`的属性保存，如：`var a = 10;` 
- 全局作用域中所创建的函数，都会作为方法保存。
- 变量声明提前：
使用`var`定义变量可以在所有代码被执行之前声明；
- 函数声明提前：
使用```function  fun(){函数体};```创建的函数会在所有的代码被执行前声明，优先级会高于`var fun = function(){函数体}`
- 全局作用域中的变量就叫全局变量


### 2、 函数作用域
 - 调用函数时创建，执行完函数时销毁；
 - 每调用一次，就会重新被创建一次；
 - 函数作用域中可以访问`全局变量`，反之全局作用域中不能访问函数作用于中的变量
 - 访问遵循`就近原则`，如果当前作用域中没有找到则会往上一级找，一直找到`全局作用域`中，如果最后都没有找到则会报错`ReferonceErro`
 - 在函数中想直接访问全局变量，可以使用`window`
 - 在函数中没有使用`var`声明的变量都会成为全局变量

 ## 3.this
 解析器每次调用函数时都会向函数内部传入两个隐含的参数`this`和`arguments`,目前先讲this。
 this参数指向的是一个对象，该对象被称为`上下文对象`，根据函数的调用方式不同，this会指向不同的对象。

 - 以函数的形式调用时:
 this永远都是windows。
 - 以方法的形式调用时：
 this便是调用该方法的对象。

**示例：**
```javascript
var name = "全局变量";
function fun(){
	console.log(this.name);//谁调用便指向谁
	}；
	
var obj = {
	name:"zhaoxin",
	sayName:fun//对象调用了fun方法
	};

var obj2 = {
	name: "xinxin",
	sayName:fun//该对象也调用了fun方法
	};

obj.sayName();
//zhaoxin
obj2.sayName();
//xinxin
```
# 四、工厂方法创建对象
通过使用工厂方法我们可以大批量的创建对象，减少代码的冗余。
语法：
```javascript
function Person(name,age,gender){
	//使用此方法工厂方法批量创建对象
		var obj = new Object();
		//开始创建对象
		obj.name   = name;
		obj.age    = age;
		obj.gender = gender;
		obj.sayName = function(){
			console.log(this.name+this.age+this.gender)
			};//添加属性与方法
			return obj;
			//return返回方法
		}
			//批量创建对象，传入属性的实参；
			var obj  = Person("赵欣,",24,"男");
			var obj1 = Person("赵欣1,",25,"男1");
			var obj2 = Person("赵欣2,",26,"男2");
			var obj3 = Person("赵欣3,",26,"男3");
}
```

使用工厂方法创建的对象使用的构造函数都是`Object`所以创建的对象类型都是Object类型，便不发区分出不同类型的对象。所以存在一定的局限性。所以还可以使用构造函数的方法。
## 1. 构造函数
构造函数就是一个普通的函数，创建的方式与普通的函数创建没有任何的区别，不同的是构造函数习惯上会将`首字母大写`

另外构造函数和普通函数的区别还在与`调用方式`的不同。
- 普通函数调用
`var per = person();`
- 构造函数调用
`var per = new Person();`



```javascript
	function Person(name,age,gender){
		//通过this把属性添加到新建的对象里面
		this.name = name;
		this.age  = age;
		this.gender = gender;
		this.sayName = fun;
			}
//将构造函数中的方法写到全局变量中好处在于节省内存空间提升运行速度
			function fun(){
			alert("大家好，我是"+this.name);
			};
		//创建Person的实例
		var per = new Person("赵欣",24,"男");
		var per2 = new Person("zhaoxin",24,"男");
		//调用
		per.sayName();
		per2.sayName()	
```
>构造函数的执行流程
>1.new 立刻创建一个新的对象
>2.将新建的对象设置为函数中的`this`
>3.执行代码
>4.将新建的对象作为返回值返回
>5.在构造函数中使用this来引用新建的对象

## 2.类与实例
构造函数就叫做`类`，通过构造函数创建的对象就称为`实例`。
我们还能通过`instanceof`来检查一个对象是否是一个类的实例。
```console.log(per instance of Person)```结果是true/false

**注意**：所有的对象都是Object的实例，Object被称为祖宗类。

## 3. 原型 Prototype
我们所创建的每一个函数，解析器都会向函数中添加一个`Prototype`属性，而prototype属性都对应着一个对象，该对象便是原型对象；

普通的函数中prototype属性是没有意义的，而当函数以`构造函数`调用时，它所创建的每一个对象都会有一个`隐含`的属性来指向该构造函数的原型对象，可以通过`_ _proto_ _`来访问该属性。

原型对象就相当于一个公共的区域，所有的同一个类的实例都能访问该原型对象，所以我们可以将对象中`共有`的内容或者方法统一的设定到原型对象中，这样便不用分别为每一个对象添加属性或者方法，也不会影响到全局作用域中就可以使每个对象都具有这些属性和方法。


**示例**
```javascript
function Dog(name,age){
		this.name = name;
		this.age  = age;
			// 		this.sayName = function(){
			// 			console.log(this.name,this.age);
			// 		}; //工厂方法写法
			//} 
		Dog.prototype.sayName = function(){
			console.log(this.name,this.age);
			};//原型对象写法
	var dog = new Dog("旺财",3);
dog.sayName();
```
此外，检查对象中是否含有某个属性时，如果对象中没有该属性，但原型对象中有，也会返回true。
>可以使用xx.hasOwnProperty("属性名"); 来检查对象自身的属性。

>**原型对象也有原型，当我们使用一个对象的属性或者方法的时候，若在原型对象中找不到，则会继续往`原型对象的原型对象`中去寻找。**
>原型的重点是Object，Object没有原型，找不到会返回`null`

## 4.垃圾回收（GC）
当一个对象没有任何的变量或者属性进行引，我们便无法操作该对象，此时该对象便是一个没有意义的垃圾。
通常情况下JS会自动回收垃圾，而我们也可以给不再需要的对象手动的赋一个`null`值来进行回收。

# 五、数组Array
数组也是对象，功能与对象类似
>普通对象：字符串作为属性名；
>数组叫元素：以数字0开始的索引来操作数组内的元素；

数组的存储性能更好，开发中常用来存储数据，
语法：
```var arr = new Array[1,2,3,4,5];```
添加元素：
```arr[0] = "a";```
```arr[1] = "b";```

## 1.length方法
我们可以使用arr.length来获取数组的长度，length方法还可以用来修改数组的长度，如大于数组的原长度，多余的位置则会被`空出来`，如果小于数组的原长度，则会删除数组后面的元素。

```javascript
//向数组最后一位添加新元素
var arr2 = [1,2,3,4,5];
	arr2[arr2.length] = 6;//在数字最后添加新元素
	console.log(arr2);
```
## 2.数组的字面量
 - 1
` var arr = [1,2,3,4,5];`
 - 2
` var arr2 = new Array (1,2,3,4,5);`
 - 3
` var arr3 = Array(10);//创建一个长度为10的数组。`

数组中的元素可以是任意的数据类型。包括对象/函数等，数组中也可以存放数组（二维数组）但开发中不常用。

## 3.数组的常用方法
### 1.push方法
向数组中添加一个或多个元素，并返回新的长度
```javascript
var arr = [1,2,3];
	var a = arr.push(4,5,6);
console.log(a);//返回新长度
```
### 2.pop方法
删除数组的最后一个元素，每调用一次删除一次。
```javascript
var arr = [1,2,3];
	var a = arr.pop();
```
### 3.unshift方法
向数组的开头添加一个或多个元素并返回新的长度

### 4.shift方法
删除数组的第一个元素，并返回被删除掉的元素

## 4.数组的遍历
```javascript

for(var i = 0; i <arr.length; i++){
	console.log(arr[i]);
}
```

也可以用`forEach（）`方法来遍历数组
```javascript
var arr = [1,2,3];
	arr.forEach(function(a){
	//使用回调函数的方法
	console.log(a);
	});
	/*在forEach的回调函数中可以传入
	三个参数，分别是1：元素、2：索引、3：正在遍历的数组
	*/
```
### 1.slice方法（切片）
可以用来从数组中提取出指定的元素
```javascript
var arr = [1,2,3];
arr.slice(0,2);
//包头不包尾
```
### 2.splice方法（功能更强大）
删除数组中指定的元素，注意：该方法会影响到原数组。

用法同上但该方法中可以添加三个以上的参数：
1.开始的位置，2.删除的个数，3.第三个参数至以后是传入的新元素。
**练习：**
```javascript
	function Person(name, age, gender){
		this.name = name;
		this.age  = age;
		this.gender = gender;
		}	
Person.prototype.toS= function(){
return "Person[name = "+this.name+" age= "+this.age+" gender= "+this.gender+"]";
				};
				
	var per = new Person("孙悟空",18,"男");
	var per1 = new Person("唐僧",28,"男");
	var per2 = new Person("蜘蛛精",17,"女");
	var per3 = new Person("猪八戒",19,"男");
			//将上面的对象放到一个数组当中
	var perArr = [per,per1,per3];
			//取出18岁以上的的人物，并存入到一个新的数组中；		  
function getAdult(arr){		  
		var newArr = [];//创建一个新的数组 
			for(var i=0; i<arr.length; i++){
				if(perArr[i].age >=18){
					newArr.push(arr[i]);							
				}else{
					console.log(0);
				}
	}
	return newArr;//返回新的数组
	}
	//调用输出
	arr = getAdult(perArr);
```

### 3.其它方法

`arr.concat(arr2)`链接两个或多个数组；

`join( )`将数组装换为一个字符串，（）中可以制定一个字符串作为连接符

`reverse()`用于反转数组

`sort()` 排序

### 4.数组去重
```javascript
	//使用splice()方法实现下列数组的去重。提示：for嵌套。
	var arr = [1,2,2,2,3,2,1,3,4,2,5];
	//遍历数组取出每一个元素
	for(var i = 0; i<arr.length; i++){
		//console.log(arr[i]);
		for(j = i+1; j<arr.length; j++){
			//外层循环执行一次内循环执行arr.length次
			if(arr[i] == arr[j]){
				arr.splice(j,1);
				j--;
			}
		}
	}
	console.log("——>"+arr);
```
# 六、函数的方法
函数的方法有如下三个
>func.call(  )
>func.apply(  )
>func(  )

使用以上三个方法都会使函数执行，但在调用`call()`和`apply()`方法的时候可以将一个对象指定为第一个`参数`，此时这个对象便会成为函数`执行时的this`。
（改变this的指向）。

- call( )方法可以将**实参**在对象之后**依次传递**
`func.call( obj,1,2,3 );`
- apply( )方法则需要将实参封装到一个**数组**当中
`func.apply( obj,[1,2,3] );`

>以函数形式调用时，this永远都是window
>以方法的形式调用时thsi是调用方法的对象
>以构造函数调用，this是新创建的对象
>以`call( )和apply( )`调用时，this是`（ ）`中指定的那个对象


## 1. arguments
arguments是一个类数组的对象；该对象不是数组，但也可以通过索引的形式来操作数据与获取长度。

在前面提到过每次调用函数时浏览器都会向函数传入两个隐含的参数，一个是`this`而另一个便是`arguments`。

在调用函数的时候，所传的实参都会在函数的`arguments`当中保存。
此外不定义形参我们也可以通过arguments来获取到实参，但不推荐这么做。

## 2.Date对象
- Date是一个内置的时间相关的对象，通过`var d = new Date();`便可以获取到当前代码执行是时刻。
- 在Date对象中我们可以传入参数从而指定固定的时间：
`var d2 = new Date("03/27/2022/   14:01:30")`

### Date对象的常用方法：
>getFullYear()————//获取年，返回年份数字
>getDate()—————//获取日
>getMonth()————//获取月份，数字0~11
>……
>其中有一个比较特殊的方法是`getTime()`
>返回的是**1970年1月1日0点0分**至今的`毫秒数`，在计算机底层中都是使用该时间戳。
>我们还可以使用`Date.now`来获取到当前的时间戳

可以利用时间戳来计算程序运行的时间：
```javascript
var d = new Date();
	console.log(d);
	//如果直接使用构造函数创建一个Date对象，则会封装当前代码的执行时间。
	//如果想指定固定的时间则：
	var d2 = new Date();
	//alert(d2.getDate());
	//alert(d2.getMonth());
	//alert(d2.getTime());
	var start = Date.now();
		for(var i = 0; i < 10; i++){
			console.log(i);
			};
	var end = Date.now();		
	console.log(end - start+"毫秒");
```

## 3.Math对象
Math虽然首字母是大写的，但它是一个普通对象，并不是构造函数，Math对象中封装的是数学相关的一些方法。
### Math对象的常用属性/方法
常用属性：
>Math.PI	———————//圆周率
>Math.SORT2————//计算2的平方根
>

常用方法：
>Math.max()————//取多个数中的最大值
>Math.min()————//取多个数中的最小值
>Math.abs—————//求一个数的绝对值
>Math.valueOf()——//求原始值
>Math.ceil()————//向上取整
>Math.floor()———//向下取整
>Math.round()——//四舍五入取整

#### Math.random()随机数
该方法可以获取一个0—1之间的二随机小数，但不包括0。
我们可以搭配上面的方法获取到任意的随机数字，示例：
```javascript
Math.round(Math.random());
//获取到0-10之间的的随机数

Math.round(Math.random()*100);
//获取一个0到100之间的随机数
```

## 4.包装类
JavaScript中为我们提供了三个包装类，包装类的作用在于可以将`基本数据类型转换为对象`的操作，这体现了万物皆对象的程序思想，在日常的JS开发中我们并不会使用到包装类。
>String()将字符串转换为String对象
>Number()将数值转换为Number对象
>Boolean()将布尔值转换为Boolean对象

虽然包装类在开发中不会使用到，但浏览器的底层是使用到他，主要作用在临时的去把包装类转换为一个对象。调用完毕后在转换为基本数据类型。

## 5.字符串的相关方法
在程序底层，字符串是以`字符数组`来存储的，所以与数组一样，我们也可以使用`.length()`和`索引`来操作字符串。此外还有如下的常用方法：
>`str.charAt(索引)`//返回字符串中的指定字符
>`str.charCodeAt`//返回字符串指定的Unicode编码
>`String.fromCharCode(编码)`//根据字符编码获取指定字符
>`str.concat("字符串1","字符串2")`//拼接两个字符串
>`str.slice(索引)`//截取内容（切片）
>`str.split`(参数)//根据参数将字符串拆分成一个数组


# 七、正则表达式

- 正则表达式可以用来定义一些字符串的规则

				1. 计算机可以根据正则表达的规则来检查字符串是否符合规则
				2. 可以将复合规则的字符串提取出来
				3. 语法：`var 变量 = new RegExp("正则表达式","匹配模式");`
				4. 匹配模式`i`:忽略大小写，`g`:全局匹配。

**构造函数示例：（更灵活）**
```javascript
var reg = new RegExp("ab","i");
	var str = "a";

console.log(reg.test(str));
//使用.test()方法，合规返回true不合规返回false
```
**字面量示例：（更简单）**
```javascript
var reg2 = /a|b/i;  
//使用数线来表示"或";
console.log(reg2.test("a,b,c"));
			
//a|b等价于[ab];
var reg3 = /[A-z]/;  

var str1  = "a1b21c13add4gedc5";
	result = str1.replace(/[a-z]/ig,"@_@");
	console.log(result);
```

## 1.字符串和正则表达式相关的方法
`split()`方法：可以更具传入的参数来将字符串拆分为一个数组，同时我们也可以传入一个`正则表达式`作为参数，这样便可以更具定义的规则来拆分数组了。
**示例**
```javascript
var str = "1a2b3c4d";

result = str.split(/[A-z]);
```
`search()`方法：可以用来搜索字符串中是否含有指定的内容。如果有则返回第一次出现的索引位置，如果没有则返回一个`-1`。同样search()方法也可以添加一个正则表达式作为参数。

`mach()`方法：可以根据正则表达式从一个字符串中提取出复合条件的字符，默认情况下只会找到第一个复合要求的字符，可以通过加上`g`来设置全局匹配模式；mach()方法还会把匹配到的内容返回到一个数组当中。
**示例**
```javascript
var str = "1a2b3c4d";

str.mach(/[a-z]/ig);
```
## 2.正则表达式的常用写法
[A-z]a到z任意字母;
[A-Z]A到Z任意大写字母;
[a-z]a到z任意小写字母;
/^a/匹配开头的字母a;
/a&/匹配结尾的字母a;
/^a|a&/匹配a开头或a结尾;
……
## 3.正则表达式的通配符与转义字符
在正则表达式中`。`表示任意字符，而`\`表示的是转义。
**其它规则**
\w  =====>任意数字和字母
\W =====>除了数字和字母
\d	 =====>任意的数字
\D =====>除了任意的数字
\s	 =====>任意的空格
\S	 =====>除了空格
\b	 =====>单词边界
\B =====>除了单词边界

## 4.邮件正则表达式练习

```javascript
/*电子邮件的规则：
	xxx.xxx@xxx.com
	任意的字母数字和下划线.任意的字母数字和下划线
	@
	任意字母和数字
	2-5位的任意字母.2-5位任意字母
*/
var reg = /^\w{3,}(\.\w+)*@[A-z0-9]+(\.[A-z]{2,5}){1,2}$/;
	var email = "trillion-star@outlook.com"
	console.log(reg.test(email));
//可以参考网上的常用正则表达式
		
```

```c
//欢迎加我VX进群交流
vx账号：-Sep07
```