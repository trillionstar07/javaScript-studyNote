
```javascript

//要求：获取1000个0-9的随机整数，然后找出里面的手机号			
		var arr = [];
//新建一个数组用于接收字符串
	for(var i = 0; i <100; i++){
		var tel = Math.round((Math.random()*9));
		arr.push(tel);
		//每次循环都将字符添加到数组中
		};
		//将数组转换成字符串
		var telNumber = arr.toString();
		//去掉字符串中的所有逗号
		var reg = telNumber.replace(/,/g, "");

/*手机号的正则表达式
^1 		   :以1开头
[3-9]      :第二位是3-9中任意数字
[0-9]{9}$  :第三位后任意9个数字
*/
var phoneReg = /1[3-9][0-9]{9}/;
		
console.log(phoneReg.exec(reg));

```

```c
//欢迎加我VX进群交流
vx账号：-Sep07
```