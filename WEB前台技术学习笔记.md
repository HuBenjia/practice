# WEB前台技术学习笔记

## js

### 2019.07.16	



###### sort

排序方法 sort
	范例：
		var ary = new Array(1,2,5,12,45,8,4);

```
alert(newAry); //按照数字进行排序
如果sort方法不传递任何参数，则按照字典顺序的ascii码值进行排序。


var newAry = ary.sort();
输出结果为：1,12,2,4,45,5,8


var newAry = ary.sort(
		function(i , j )
		{
			return i - j;
		}
	);
	
输出结果为：1,2,4,5,8,12,45
```



例题：

​	排序扑克牌    （J,Q,K,A,2.....,10,大王，小王）	     从小到大排序，2算大的。

<script type="text/javascript">
		var shunxu = [3,4,5,6,7,8,9,10,'J','Q','K','A',2,'小王','大王'];
		var ary = [2,6,5,4,7,8,9,3,'J','K','大王','Q','A','小王'];
		ary.sort(function(i,j)
		{
			return shunxu.indexOf(i)-shunxu.indexOf(j);
		}
		);
		alert(ary);
 </script>

![1563500251885](C:\Users\胡 佳\AppData\Roaming\Typora\typora-user-images\1563500251885.png)



###### indexOf 方法

​			![1563333830178](C:\Users\胡 佳\AppData\Roaming\Typora\typora-user-images\1563333830178.png)

i.toString().indexOf("3") != -1

比如说你的i是一个整数12565675，从左往右开始，i.toString就是把你的i转换成String类型“12565675”，然后再调用String的indexOf(String str)方法，就是返回指定子字符串在此字符串中第一次出现处的索引，假如你的字符串里面没出现过str，就返回-1。总得来说，就是判断这个数里面有没有3，没有就返回-1



###### ceil()

ceil 方法：大于等于其数字参数的最小整数。 

3.4 ==》4



###### floor()

floor 方法：小于等于其数值参数的最大整数。 
		3.4 ==》3		



###### round 方法：四舍五入到整数

​	Math.round(3.8);   ------>  4

​	Math.round(3.4);   -------> 3

例题：

	写一个函数，函数原型如下
	function myRound( num , p )
	{
		//写实现精确点小数点后几位的函数
	}	
	var r = myRound( 34.567 , 2 ) ; == > 34.57
	var r = myRound( 34.5678 , 3 ) ; == > 34.568


<script type="text/javascript">
    function myRound (num,p) {
	var j = 1;
	for(var i = 0;i < p;i++){
		j*=10;
	}
	return Math.round(num*j)/j;
}
alert(myRound(23.5678,2));
</script>	                                结果为：23.57





###### new Boolean()

​        new Boolean("") ==> false
​		new Boolean("0") ==> true



###### parseInt(i)

   	 var i = "1.7";
		parseInt(i) ; ==>1



###### Math.random(  ) 产生随机数

**	Math.random()是令系统随机选取大于等于 0.0 且小于 1.0 的伪随机 double 值**



例题

写一个函数，函数原型如下
function myRandom( num )
{
	//写一个实现求随机整数的函数
}
var r = myRandom(100); ==> [0,100)



<script type="text/javascript">
    function myRandom(num){
	num = parseInt(num);

	return parseInt(Math.random()*num);
}
alert(myRandom(100));
</script>         产生一个1到100的随机整数





###### new Date()

​	获取当前标准时间

![1563338369401](C:\Users\胡 佳\AppData\Roaming\Typora\typora-user-images\1563338369401.png)

###### getTime()

​	getTime 方法：得到从1970/01/01标准时间到该时间之间经历的毫秒数



###### getFullYear()   

​	得到年   new Date().getFullYear()    ------->  2019

###### getMonth()

​	得到月 ，0-11    new Date().getMonth() + 1      --------> 7

###### getDate() 		

​	得到1-31之间的一个数字   new Date().getDate()   --------->17



例题

 小明的爸爸要退休了，小明要继承爸爸的衣钵，
爸爸是打鱼的，爸爸说，要三天打鱼两天晒网。
爸爸的退休时间为2015/2/3，请问小明今天在干什么



<script type="text/javascript">
	function getDay(year, month, day){
		var d = new Date(year,month,day);
		var today = new Date();
		return parseInt((today.getTime()-d.getTime())/86400000);
        }
    var day = getDay(2015,2,3)%5;
	if(day > 3){
		alert("晒网");
	}else{
		alert("打鱼");	
	}
</script>



小明是1999/2/5出生的，小明的妹妹于569天后
出生，请问小明的妹妹几年几月几日出生

<script type="text/javascript">
    function gettime(year, month, day) 
    {
		var d = new Date(year,month,day);
		return parseInt(d.getTime()+569*86400000);
	}
    var day = new Date(gettime(1999,2,5)) ;
	var s;
	s=day.getFullYear()+"/";
    s+=day.getMonth()+1+"/";
    s+=day.getDate();
	alert(s);
</script>



###### join

 join 
	范例：
	var ary = new Array(1,2,"张三丰");
	var str = ary.join(".");
	alert(str);                                              输出结果:    1.2.张三丰



######  document.getElementById(" ") 

得到的是一个对象，用 alert 显示得到的是“ object ”，而不是具体的值，它有 value 和 length 等属性，加上 .value 得到的才是具体的值！



###### document.getElementById("").innerHTML="";



<script type="text/javascript">
function fun() {
    //弹窗输出输入的内容 <input type="text" id="name"/>
	var str = document.getElementById("name").value;
    alert(str);

    //在输入框右侧输出相关信息 <span id="mes"></span>
    // var str = document.getElementById("mes").innerHTML="";

}
</script>

<body>
    <input type="text" id="name"/><span id="mes"></span>
	<input type="button" value="提交" onclick="fun()"/>
</body>



###### reg.test(card) 

​	验证正则表达式

​       var reg = /^-?\d+\.?\d{0,2}$/;
​	   if(reg.test(card) === false)  

 

###### 常用的正则表达式整理

​	验证邮政编码	/^\d{6}$/

​	验证固定电话	/^\d{3}-\d{8}|d{4}-\d{7}$/

​	验证身份证号	/^\d{15}|d\{18}|d{17}[x X]$/

​	验证移动电话	/^\d13\d{9}$/

​	验证小数点后两位	/^-?\d+\.?\d{0,2}$/

```
	范例：23.568 ==> false
	45.6 ==> true
	45 ==> true
```

​	验证电子邮箱地址 ![1563345632495](C:\Users\胡 佳\AppData\Roaming\Typora\typora-user-images\1563345632495.png)







### 2019.07.17

###### 	onclick

​       onclick 属性由元素上的鼠标点击触发

	<script type="text/javascript" language="javascript" src="js/js1.js">z`在·````````````	```	``		```				`													C																			



###### setInterval()

​	指定时间间隔调用一次指定方法

​    window.setInterval("clock()",1000);    每隔一秒调用一次clock

	<html>
	<head>
	<meta charset="UTF-8">
	<title>Insert title here</title>
	<script type="text/javascript">
		window.onload=function(){
			window.setInterval("clock()",1000);   //每隔一秒调用一次clock
		}
		function clock() {
			var date = new Date();   //黄金
			var hour = date.getHours(); 
			var min = date.getMinutes();
			var seconds = date.getSeconds();
			document.getElementById("div1").innerHTML=hour+":"+ min+":"+seconds;
			
			//将内容发布到div1
		}
	</script>
	</head>
	<body>
		<div id="div1"></div>
	</body>
	</html>



######  document.getElementsByName("");

<script type="text/javascript">
	function del() {
		var text = document.getElementById("text"); //只能获取一个
		var password = document.getElementById("password");
		var radio = document.getElementsByName("1");    //能获取多个
	}
</script>

	<label>密码框：</label>
	<input type="password" id="password" value="234">
	
	<label>单选按钮：</label>
	<input type="radio" name="1" checked="checked">
	<input type="radio" name="1" checked="checked">
	<input type="radio" name="1" checked="checked">
	






var state = document.getElementById("checkbox1").checked;

获取全选按钮是否被选中



var checkbox2 = document.getElementsByName("checkbox2");

获取name="checkbox2"的状态的数组

<script type="text/javascript">
	function sellall() {
		var state = document.getElementById("checkbox1").checked;
		var checkbox2 = document.getElementsByName("checkbox2");
		for(var i = 0;i<=checkbox2.length;i++){
			checkbox2[i].checked = state;
		}
	}
</script>
	<input type="checkbox" id=checkbox1" onclick="sellall()"/>全选<br>
	<input type="checkbox" name="checkbox2"/><br>
	<input type="checkbox" name="checkbox2"/><br>
	<input type="checkbox" name="checkbox2"/><br>


######  formula.value

​	计算器方法



###### select  下拉菜单



<select id="sel1" multiple="multiple" style="float: left;">
		<option selected="selected">宫保鸡丁</option>
		<option value="">九转大肠</option>
		<option value="">烤乳猪</option>
		<option value="">烤全羊</option>
		<option value="">烤羊腿</option>
	</select >

<option selected="selected">被选中







## jquery



### 2019.07.18



###### js库  一定要引入js库

​			 路径一定是绝对路径

###### jquery 能干什么

​	有良好的兼容性

​	方便获取dom对象

​	方便动态生成dom对象，对dom进行替换

​	方便注册及使用事件

​	很容易可以实现各种特效

​	提供了丰富的异步提交方法，实现无刷新技术

​	and so on!

###### jQuery 核对象介绍

​	 核对象就是jQuery

​	$(函数)：dom加载完毕后，我要干的事

​	$(字符串)：选择dom对象，返回的事jQuery对象

​						jQuery对象是没有办法用dom对象的方法和属性的

​	

jQuery转换为dom 对象的方式：



###### required 

```
<input required="required">
```

```
<form action="demo_form.asp" method="get">
  Name: <input type="text" name="usr_name" required="required" />
  <input type="submit" />
</form>

```

required 属性规定必需在提交之前填写输入字段。

如果使用该属性，则字段是必填（或必选）的。

注释：required 属性适用于以下 <input> 类型：text, search, url, telephone, email, password, date pickers, number, checkbox, radio 以及 file。



###### eval()

```
<script type="text/javascript">

eval("x=10;y=20;document.write(x*y)")   // 200

document.write(eval("2+2"))   //4

var x=10
document.write(eval(x+17))   //27

</script>
```



######  attr() 

​    attr() 方法设置或返回被选元素的属性值。









### 2019.07.19

###### 	ready(fn)

```
$(document).ready(function(){
  // 在这里写你的代码...
});


等效于
$(function(){})
```





