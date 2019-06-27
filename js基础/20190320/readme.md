# JS基础
## js输出内容
* alert()<br>
  在页面中弹出对话框 <br>
  早期js调试使用

* console.log()<br>
  将信息输入到控制台<br>
  用于js调试 常用

* prompt()<br>
  弹出对话框 于接收用户输入的信息
  
* doucument.write()<br>
  在页面输出消息或者标签 几乎不用

* 注释 ctrl+/

<hr>

## js变量
### 定义:变量是用来存储数据的容器
* 创建一个变量: var关键字 比如var a; 声明一个变量a
* 给变量赋值: a = 100; 这里的 = 是赋值运算符 
* 简写 var a = 100;
* 可以多个变量一次声明 : var a,b,c,d;
* 一个变量只能存储一个值

## 变量的命名规范
* 名字必须以字母,下划线,美元符号开头,后面可以跟字母,下划线,美元符号和数字
* 不能以数字或者纯数字开头来定义变量名
* 不推荐使用中文
* 不能使用特殊符号
* 在js中是严格区分大小写的!
* 不允许用js关键字和保留字

## 简单数据类型 
* Number 数字类型<br>正负数 小数 Infinity NaN
* String 字符串<br> 凡是用双引号或者单引号保卫的内容的都是字符串
* Boolean 布尔数据类型<br> 只有两个值 一个是true 一个是falsse 实际运算中 true=1,false=0
* undefined 变量未初始化 
* null 变量未引用 <br>一般用来表示占位 值为空

## 复杂数据类型
* object 对象 
* 数组 

## typeof检测数据格式
* typeof 返回的值 number string boolean undefined object function

## 算术运算符
* 加号<br>
  两个作用 1.数学上的加法 2.字符串拼接
  两个数字类型的变量相加，得到的是一个数字类型。一个数字类型和一个字符串相 加，得到的是一个字符串(拼接)。NaN Not a Number,Infinity: 无

* 减号<br>
  两个数字类型的变量相减，得到的是一个数字类型。
  一个数字类型和一个数字字符串相减，得到的是一个数字类型。（数据类型隐式转换）
  一个数字类型和一个非数字字符串相减，得到的是NaN,是一个数字类型。

* 除号<br>
  两个数字类型的变量相除，得到的是一个数字类型。
  一个数字类型和一个数字字符串相除，得到的是一个数字类型。
  一个数字类型和一个非数字字符串相除，得到的是NaN,是一个数字类型。
  0做为除数的时候，得到结果 Infinity （无限大），是一个数字类型。
 
* 取余数
* 优先级 有()先计算()里面的 
* 带操作的赋值运算

# 补充:JS的显示转换与隐式转换

### JavaScript 是一种弱类型或者说动态语言.这意味着你不用提前声明变量的类型，在程序运行过程中，类型会被自动确定

#### 基本类型<br>
  运算符操作时 转换类型

* 加号运算符<br>
  String+其他类型时，其他类型都会转为 String；其他情况，都转化为Number类
型
注： undefined 转化为Number是 为'NaN'， 任何Number与NaN相加都为
NaN

# Date和Math对象使用
## date用法
* Date() 返回当前时间日期
* getDate() 返回一个月中某一天
* getMonth() 返回月份(以数组形式存储 从0到11)
* getFullYear() 返回年 
* getHours() 返回小时部分
* getMinutes() 返回分钟部分 
* getSeconds() 返回秒数
* getDay() 返回一周之中某一天 0(周日)到6(周六) 之间的一个整数



		var date = new Date();
		var year = date.getFullYear(),
    		month = date.getMonth(),
    		day = date.getDate(),
    		hour = date.getHours(),
    		minute = date.getMinutes(),
    		second = date.getSeconds();
    		weekend = date.getDay();
		var dateStr = year + "-" + (month+1) + "-" + day + "星期" + weekend +" "+ hour + ":" + minute + ":" + second ;

		console.log(dateStr);	

## Math对象
### Math.ceil()天花板函数
* 返回一个数字的整数部分(向上舍入) 
* 不会对数字进行四舍五入

 	 Math.ceil(2.3)
  	
	3




### Math.floor()地板函数
* 向下舍入

### Math.max(x,y)
* 返回x,y之间的最大值

### Math.min(x,y)
* 返回x,y之间的最小值

### Math.random()伪随机
* 返回0-1之间的数值 范围 [0,1)

#### 任意范围的随机数Math.floor(Math.random() *数量+ min)


### Math.pow(x,y)
* 返回x值得y次方

### Math.round(x)
* 把一个数字舍入最接近的整数



# 比较运算符
* 大于
* 小于
* 大于等于
* 小于等于
* ==
* === 全等于 首先对比类型再对比值 较常用
* != 不等于
* !== 不全等于 4

# 关系运算符 
## 得到的结果都是布尔值 
### 字符串比较的是ASC码  ==这个符号可以验证字符串是否相同


# 逻辑运算符
## && (与/且) ||(或) !(非) 
### 参与逻辑运算的，都是布尔值。也就是说，只有true、false才能参与逻辑运算，得到的答案，仍然是布尔值
* && 都真才真 返回值:先看表达式转换成布尔值得结果 
* || 只要有一个真就为真 返回值:遇到真就返回
* ! 相反  !!就是将一个值变成布尔值

# undefined null NaN "" 0 false 对应的布尔值====> false

### 连比的写法: console.log(3 < 2 && 2 < 4);


# if语句 
## 如果...那么...否则...


	if(条件表达式){
		条件为真的时候做的事
	}else{
	   条件为假的时候做的事
	}



### 多分支的if语句和跳楼现象

# if语句的嵌套


 
# 三元运算符
rs = 5<3?'明天不上班!':'明天上班!';

# 代码调试
* 程序完成后点击f12
* 设置断点
* 运行程序
* 一步一步执行
* 直接选择变量名 点击鼠标右键选择add watch添加监视



#  Break 语句
##  在当前循环体内,只要代码遇到break,程序立马结束循环.当前循环指的是break语句所在的循环体.

# Continue 语句
## continue语句值得是跳出本次循环,该语句后面的代码不再执行.

# Switch 语句
## 适合种类较少的判断(已知多少种)
### Switch 语句后面的变量数据类型必须和case后面的数据类型保持一致
语法



    Switch(变量n){
		case 10:
			执行的代码;
			breaak;
		case 20;
			执行的代码;
			break;
		default:
			执行的代码;
			break;}


## Switch语句可一堆变量进行集体判断

# While 循环
## While循环的过程中,首先在While循环内部定义一个变量,然后判断条件.循环一定要有跳出条件

语法

	while(条件表达式){
	当条件表达式结果为true,会一直执行while循环体内的代码。
	当条件表达式的结果为false，while循环不再执行。
	}

# For 循环
	
	for(var i = 0 ; i <= 10; i++){
		循环体代码
	}

## 执行顺序:
* 首先进行变量初始化,并进行条件判断
* 如果条件结果为true,那么执行循环体内的代码
* 判断条件是否为true,继续执行循环体内代码。否则跳出循环


# 数组 Array
## 1.定义

* 通过对象方式创建数组 var arr = new Array();
* 直接创建数组 var arr = [];
* 驼峰命名,如果是名字的数组 name Arr

## 2.赋值 数组中通过下表的方式进行赋值.下标从0开始.arr[0]=123;或者直接初始化赋值 var arr = [1,2,3,4,5];

## 3.length属性 通过数组名.length获取数组长度 (元素个数 ) arr.length

## 4.数组遍历(两种方法)

	var arr = ["zhangsan","jim",14,true,12,1,56];
	for(var i = 0; i < arr.length; i ++){
		console.log("i=======>" + i + "arr[" + i + "]=====>" + arr[i]);
	}

<br>

	for(var i in arr){
		console.log("i=======>"+ i + "arr[" + i + "]=====>" + arr[i]);
	}



## 5.数组合并 concat()方法
### 将一个数组与另一个或多个数组或非数组元素合并并返回合并后的数组

		var arr = [1,2,3,4];
		var arr1 = [true,false,"split"];
			
		arr = arr.concat(1,2,["a","b","c"]);
		console.log(arr);

## 6. join() 将数组转换成字符串
### 作用是将数组各个元素是通过指定的分隔符进行连接成为一个字符串，并返回字符串。语法： arrayObject.join(separator)数组名.join(符号);参数 separator 可选。指定要使用的分隔符。如果省略该参数，则使用逗号作为分隔符。


	var arr = [1,2,3,4,5];
	arr = arr.join(" ");
	console.log(arr);
## 7. split() 将字符串转换成数组
### split() 方法用于把一个字符串分割成数组，并返回数组。语法：stringObject.split(separator,howmany)参数 separator 可选。指定要使用的分隔符。如果省略该参数，则创建的数组只有一个元素。howmany 可选。该参数可指定返回的数组的最大长度

	var str = "smith,john,gina,white,kate";
	var arr = str.split(",", 3);
	console.log(arr);


## 8. 数组的增删改查
### unshift() push() 从数组前，后插入一个或多个元素，并返回数组的长度

### shift() pop() 删除数组第一/倒一的元素，并返回被删除的元素

## 9. 冒泡排序，选择排序
### 选择排序（Selection sort）是一种简单直观的排序算法。它的工作原理是每一次从待排序的数据元素中选出最小（或最大）的一个元素，存放在序列的起始位置，直到全部待排序的数据元素排完。




# 函数
## 函数，就是一种封装，就是将一些语句封装到函数里面，通过调用的形式，执行这些语句，达到复用的效果，类似模块化封装
### 函数的编程思想：高内聚，弱耦合

### 三种创建函数的方式：函数声明，函数表达式，构造函数
	function fn(){
		console.log('aaa');
	}
	console.log(typeof fn);
<br>

	var fn1 = function(){
		console.log("匿名函数");
	}	
	fn1();			

