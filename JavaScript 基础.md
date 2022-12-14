# 初识JS

* 引入外部 JS    <script src = "文件链接"></script>  *中间不允许写代码*
* 注释  //  (ctrl + /)    /\*  \*/  (atl + shift + a)
* alert()  弹出警示框    console.log()  控制台输出    prompt()  弹出输入框
* 命名规范  **变量一般用名词，函数一般用动词**

# 变量

* 声明  var age;    赋值  age = 12;    var age = 12;
* var 变量名 = prompt('内容');    接收输入赋值  *接收的都为字符串型*
* 声明多个变量用逗号隔开    var ~ = ~, ~ = ~, ...;
* 命名变量  使用驼峰命名法  eg.  className    *name 在一般浏览器中有含义，最好不要做变量名*

>JS 的变量类型是在运行过程中得到值才确定的 *动态语言，变量的数据类型可以变化*

# 数据类型

## 简单数据类型

Number、Boolean、String、Undefined*未定义类型*、Null*声明为空*

### 数字型 Number
* num = 010  八进制， num = 0xa  十六进制
* Infinity  无穷大    -Infinify  无穷小    NaN *not a number*  非数值
* JS 中的最大值和最小值  Number.MAX_VALUE | Number.MIN_VALUE
* isNaN()  判断非数字，不是数字则返回 true
* undefined 与数字相加为 NaN

### 字符串型 String
>变量加了引号的都是字符串型
>推荐用单引号框起来 *因为 html 标签用了双引号*

* 嵌套原则  外单内双（或外双内单）
* 字符串转移字符（写在引号里）  \\n 换行 \\\\ 斜杠 \\t tab缩进 \\b 空格
* 字符串 + 任何类型 = 字符串    *拼接*
* a.length  获取字符串长度

### 布尔值
true、false

## 数据类型常用方法

* 转为字符串    变量.toString  强制转换 String(变量)  加号拼接字符串 num + '' *隐式转换*
* 转为数字    parseInt(string) 只保留整型数  parseFloat(num) 转换为浮点型  Number('12') 强制转换
	* 识别的第一个值为数字才可进行转换，否则返回NaN
* 运用运算符 “ -, \*, / ” 后跟数字可进行隐式转换
>用 prompt 接收的值是字符串型，用作运算时需要转换为数字型
* 转为布尔型  Boolean()    " ' ', 0, NaN, null, undefined" 返回结果都是 false 其余为true

## 运算符|逻辑运算符

### 运算符
\+ \- \* \/ \%    
>先乘除后加减
>使用浮点数运算会有一些误差，浮点数比较相等会出错，尽量避免直接运算

++num | num++

18 == '18'  结果为 **true**    18 === '18' 结果为 **false**
 ==  值相同为 true        ===  值和类型相同才为 true

### 逻辑运算符
&&  与运算*同真为真*，  ||  或运算*有真为真* ， !  取反
>**逻辑中断： 有多个表达式（值）时，左边可以确定结果时，将不再运算右边的表达式（值）**
>逻辑与  左边真返回右边，为假则返回左边
>逻辑或  左边为真返回左边，否则返回右边
>也称**短路运算**

### 执行顺序自己查

---

# 流程控制

## if 
```javascript
if() {
	执行语句
} else {
	
}    //双分支语句

if(条件) {
	执行语句
} else if {
	
} else if {
	
} else {

}    //多分支语句

条件表达式 ? 表达式1 : 表达式2 
```

## switch
```javascript
switch(表达式) {
	case 值:
	语句;
	break;
	...
}
```

## while
```javascript
while(条件) {
	...
}

do {
	...
} while(条件);
```

>continue 跳出本次循环，继续执行剩下循环
>break 跳出整个循环

# 数组

## 创建数组
* new方法    var arr = *new* **A**rray();  创建了一个空数组
	* new Array(2)  表示数组的长度为2
* 数组字面量        var arr = \[\];    \[\] 代表数组
>数组的元素用逗号隔开
>获取数组  arr\[1\]  1表示下标号

## 数组方法

* 利用循环遍历数组  *该方法可使数组转为 字符串*
* arr.length    返回数组长度|个数
>新增数组长度    arr.length = 5 (目标长度)  or  arr\[5\] = 'a'  使数组第6个元素为‘a’ *可用作新增或者替换原来元素*

>给已有数据的**数组名**进行赋值，将会替换所有的内容，使数组消失

# 函数

## 定义
*function fn() {
	函数体
}*   or
*var fn = function() {
	函数体
}*
>已有定义的函数调用，在代码中直接打    函数名();

## 参数
*实参多于形参时，取形参个数的实参数进行运算；
实参少于形参时，多余的形参会定义为 undefined，最终结果要由运行结果决定*

## 返回值 return
* 函数内部遇到 return 就将 return 的内容返回
* **return 可以终止程序（退出循环），在函数里 return 后的代码将不执行**
* 只能返回一个值，如 return num1, num2; 只返回 num2，如果想返回多个值可利用数组的形式
* 整个函数调用时，如果没有 return，则函数自身为 undefined

## 函数的内置对象 arguments *伪数组*
>*伪数组*
具有数组的 length 属性 | 按照索引的方式进行存储 | 没有真正数组的一些方法，如：push()  pop() ...
* 在函数内部的 arguments 里面以数组的形式存放了所有的传递过来的实参


# 作用域[[作用域]]

# 预解析[[预解析]]

---

# 对象
>JS 中指一组无序的相关属性和方法的集合，类似 C语言 的结构器

## 创建对象 
>*键值对*    属性名为 键，属性值为 值，对象是由多组键值对组成的
* 字面量  {}    var obj = {}  创建了一个空对象
* var obj = {
		属性1==: ==元素==, ==
		属性2==: ==元素==, ==
		属性3==: ==function() { ... }==, ==
		...
	}
* var obj = new **O**bject();

## 使用对象
* obj==.==属性名  “ . ” 可以理解为 “的”    对象的属性
* obj\[=='属性名'==\]     用中括号括起时需要在属性名加引号
* obj.函数名()   调用对象中的函数也要加括号

## 增加属性
* obj.属性名 = ‘ ... ’;    跟平时的赋值相同，包括定义函数方法也相同

## 构造函数
```javascript
function 构造函数名(形参1, 形参2, ...) {
	this.属性 = 值;
	...
	this.方法 = function() { ... }
}
new 构造函数名();  //调用构造函数
```
### 调用 
**必须使用 new** [[new 关键字]]
eg. function Star(形参1, 形参2, ...) { ... } 
		var obj = new Star(实参1, 实参2, ...);  *函数名首字母要大写*
**构造了函数之后，每 new Star(); 一次之后就创建了一个新的对象**

# 一些方法

## 遍历对象
*使用 for ... in ...  遍历对象*    使用了循环
eg. for(var k in obj) {
		console.log(k)  *k得到的是属性名*
		console.log(obj\[k\])  *obj\[k\]得到的是属性值*
	}

## 内置对象
>JS 中有 3 种对象：自定义对象（基础）、内置对象（*属于 ECMAscript*）、浏览器对象（JS APIs）
可查 MDN 文档学习

## Math 数学对象

*Math.PI 圆周率 | Math.floor() 向下取整（变小） | Math.ceil() 向上取整（变大） | Math.round () 四舍五入 | Math.abs 绝对值（有隐式转换） | Math.max() Math.min() 最大最小值*

*Math.random() 返回一个包括 0 但不包括 1 的随机浮点数*
...

## 日期对象
>Date()  处理日期和事件 *该方法为构造函数，创建时需要 new 来调用创建*
>eg.  var date = new Date();
* 直接使用 Date() 返回的是当前的时间（无参数）
* 参数在 Date() 里的写法
	* 数字型  2022, 7, 20  不需要引号  这时返回的月份会变成 8 月（月份从 0 月算起到 11 月）
	* 字符串型  ‘2022-7-20 17:03:32’  需要加引号  （最常用）

### 日期格式化  
*var date = new Date();*
* var year = date.getFullYear();
* var month = date.getMonth() + 1;
* var dates = date.getDate();  日期
* var day = date.getDay();  返回星期数 *从 0（周日） 开始到6*
* ...
[[格式化年月日、时分秒]]  

### 时间戳  [[倒计时（距离2022.9.1）]]
* date.valueOf() | date.getTime()  *返回距离 1970.1.1 号的总毫秒数*
* var a = +new Date()  返回的也是总毫秒数（最常用）
* Date.now()  H5 新增

## 数组对象
*var arr = \[\];*

### 检测是否是否为数组
* arr instanceof Array  返回 true 或 false
* Array.isArray(arr)  返回 true 或 false  H5新增，ie9 以上支持

### 添加、删除数组中的元素
* arr.push(元素1, 元素2);  在数组最后追加一个或多个元素
* arr.unshift();  在数组开头添加一个或多个元素
>添加完毕后，返回的结果为新数组的长度  eg.  console.log(arr.push('a'));  会输出添加了元素后的数组长度

* arr.pop();  删除数组最后一个元素(不需要参数)
* arr.shift();  删除数组第一个元素
>删除完毕后，返回结果为删除的元素

### 数组排序
* arr.reverse();  翻转数组
* arr.sort();  冒泡排序（第一个元素）
	* arr.sort(function(a, b)) {
			return a - b; 升序 | return b - a 降序
	}

### 数组索引
*[[数组去重案例]]*
* arr.indexOf(元素);  返回该元素的索引号，只返回第一个满足条件的（从前往后），没找到则返回 -1
* arr.lastIndexOf(元素);  从后往前找，返回索引号

### 数组转换为字符串
* arr.toString();  
* arr.join(分隔符);  默认为使用逗号作为分隔符，使用 join 可以自定义分隔符

### 其他方法
* concat()  连接两个或多个数组，不影响原数组，返回一个新的数组
* slice(begin, end)  截取数组，返回被截取后的一个新数组
* splice(开始的序列号, 删除的个数)  返回被删除后的新数组，会影响原数组

---
[[基本包装类型]]

## 字符串对象
var str = ' '
>**字符串**(其他类型不是）不可变：创建了字符串就会有一个地址存放着字符串，将变量的字符串改变实际是将变量的地址指向改变了

>不要经常拼接字符串，这样会开辟很多新空间，会占许多资源

>字符串所有的方法，都不会修改字符串本身，操作完成会返回一个新的字符串

### 根据字符返回位置
* str.indexOf(目标字符, 开始的位置);  返回索引号，无则返回 -1
* str.lastIndexOf();  从后往前，返回索引号

### 根据位置返回字符
* str.charAt(位置);  返回指定位置的字符
* str.charCodeAt(位置);  返回指定位置的字符的ASCII码
* 变量名\[位置\]    H5新增，ie8+ 支持，和 charAt() 等效

### 拼接字符串及截取字符串
* str.concat(str1, str2, str3);  连接两个或两个以上的字符串，等效于 + ，+ 更常用
* str.substr(start, length);  从 start 位置开始，取 length 的个数 **重点**
* str.slice(start, end);  |  str.substring(start, end);

### 其他方法
* str.replace(被替换的字符, 替换为);  只替换第一个符合的字符
* str.split(分隔符);  将字符转换为数组，分割位置取决于分隔符
* str.toUpperCase()  转换大写
* str.toLowerCase()  转换小写

# 简单类型与复杂类型
>简单类型又称基本数据类型或值类型
>复杂类型又称引用类型

* 值类型：简单数据类型在存储时变量中存储的是**值本身**，因此叫值类型
	* string | number | boolean | undefined | null
	* null 返回的是空对象，如果有个变量暂时不清楚存什么，可以给 null
>直接在栈里开辟空间存放值

* 引用类型：复杂数据类型在存储时变量中存储的仅仅是**地址（引用）**，因此叫引用数据类型
	* 通过 new 关键字创建的对象（系统对象、自定义对象），如 Object | Array | Date 等
>先在栈里存放地址（十六进制），然后这个地址指向堆里的数据

## 堆和栈
>JavaScript 中没有堆栈概念

* 栈（操作系统）：由操作系统自动分配释放存放函数的参数值、局部变量的值等。
>**简单数据**类型存放到**栈**里
* 堆（操作系统）：存储复杂类型，一般由程序员分配释放，若不释放，则由垃圾回收机制回收
>**复杂数据**类型存放到**堆**里

