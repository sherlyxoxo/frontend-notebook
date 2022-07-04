# 1.简介
## 1.1 概念
		JavaScript 是一种运行在客户端（浏览器）的编程语言
## 1.2 作用
1. 网页特效 (监听用户的一些行为让网页作出对应的反馈)<br />2. 表单验证 (针对表单数据的合法性进行判断)<br />3. 数据交互 (获取后台的数据, 渲染到前端)<br />4. 服务端编程 (node.js)

## 1.3 组成
ECMAscript 语言基础<br />DOM 文档对象模型<br />BOM 浏览器对象模型<br />dom，操作文档：页面元素移动、大小、添加删除 <br />bom，操作浏览器<br />权威网站：MDN

## 1.4 script标签的位置
​    外部式（通过src引入外部js文件，引入后script标签里面不要再写代码。）<br />	内部式（文档末尾 script写在</body>上面）<br />	内联式（直接写在html标签内部（vue里会用到））

```html
 内联式
<button onclick="alert('月薪过万') "> 点击我</button>

内部式
 <script> 
  alert('努力，奋斗')
</script>

外部式
<script src="./my.js"></script>
```
注意：<br />	1. <script>可以定义在html页面的任何地方。但是定义的位置会影响执行顺序。<br />	2. <script>可以定义多个。
## 1.5 JavaScript注释
   单行注释<br />		// 用来注释单行文字（  快捷键   ctrl  +  /   ）<br />	多行注释<br />		/* */  用来注释多行文字（ 默认快捷键  alt +  shift  + a ） 

## 1.6  JavaScript结束
分号； 换行符也可以结束，没有换行就要加分号；结尾 可写可不写
# 2.基础语法
## 2.1 输入输出语法
### 	1）输入语法
​	prompt（''）

### 	2）输出语法
​        alert()<br />		console.log()<br />		document.write()<br />		输入字符串要加’‘

## 2.2 字面量
​       在计算机科学中，字面量（literal）是在计算机中描述事/物<br />		123 是数字字面量<br />		'黑马程序员'  字符串字面量<br />		[] 数组字面量   {}对象字面量

## 2.3 变量
### 1）概念和作用
计算机存储数据的“容器”
### 2）变量的使用
#### ①声明变量
let 变量名（标识符） 
#### ②变量赋值 
变量名（标识符） = <br />等号左右要加空格 <br />变量不要加引号 <br />变量里的值一次只能存一个 
#### ③变量初始化
声明的时候就 赋值 <br />let 不允许多次声明一个变量，但是可以一次声明多个变量，用逗号隔开<br />	
```html
 <script>
        // let声明变量   age 变量名
        // let age
        // 赋值
        // age = 18
        // age = 19

        // console.log(age)
     

        // 2变量的 初始化  声明变量的时候直接赋值
       let age = 18, uname='哈哈哈'
       age = 19
       console.log(age)
       document .write(uname)

      
    </script>
```
#### ④案例：交换变量
```html
<script>
  let num1 = 10, num2 = 20
  let temp 
  temp = num1
  // 或直接let  temp = num1 
  num1 = num2
  num2 = temp
  
  console.log(num1,num2)
  
    </script>
```
通过临时变量来交换变量的值, <br />出现新变量等于旧变量的时候先声明变量，再赋值 <br />log(变量1，变量2）中间隔开		

### 3）变量的本质
内存：计算机中存储数据的地方，相对于一个空间， <br />变量是程序在内存中申请的一块用来存放数据的小空间
### 4）命名规则和规范
1.规则 <br />1）不能用关键字（let var for if等） <br />2）只能用下换线、字母，数字服务组成，且数字不能开头 <br />3）字母严格区分大小写

 2.规范 <br />起名要有意义<br />小驼峰命名法 <br />第一个单词首字母小写，后面每个单词首字母大写 <br />myFirstName<br />		
## 2.4 数组
array 数组，可以按顺序保存多个数据<br /> let arr = [数据1，数据 2，... ] <br />计算机重点 编号从0开始，数据1的编号是0 <br />数据的编号又叫索引或下标 <br />数组名[ 索引] <br />1.数组中保存的每个数据叫数组元素 <br />2.下标，数组中每个数据的编号 <br />3.长度，数组中数据的个数，通过数组的length属性获得
```html
<script>
  //    let arr = ['马超', '黄忠', '关羽', '关羽', '张飞', 18 ]
  //    console.log(arr);
  //    console.log(arr[0]);
  //    console.log(arr[5]);
  
  let arr = ['星期一', '星期二', '星期三', '星期四', '星期五', '星期六', '星期日']
  console.log(arr[6])
  //    长度，数组中数据的个数，通过数组的length属性获得
  console.log(arr.length)
  
    </script>
```

## 2.5  数据类型
### 1）概念和作用
​	   1. 更加充分和高效的利用内存<br />		2. 也更加方便程序员的使用数据

### 2）基本数据类型
#### ① number 数值型
数字：整数、小数、正数。。<br />（js赋值后才知道变量是什么类型）<br />数字型是蓝色，字符串是黑色
#### ② string字符串
 单引号' '，双引号"" 或反引号`   



包裹的数据都叫字符串，推荐单引号 <br />引号必须成对使用 <br />单双引号可以互相嵌套，外单内双，外双内单<br />字符串拼接<br />' ' + ' '  <br /> 字符串 + 数字 =字符串 <br />数字+数字=数字
```html
<script>
 // 利用 + 做拼接
        console.log('我是' + 'ahhahh')
        // 字符串 + 数字 =字符串
        console.log('我今年年龄是' + 18)
        let age = 91
        console.log('我今年年龄是' + age);
        // 数字+数字=数字
        console.log(18 + age);
      
        // 用户输入名字
        // 页面输出的是： 我的名字是xxx
        let name = prompt ('请输入名字：')
        document .write ('我的名字是' + name)
  
    </script>
```
模板字符串：作用：拼接字符串和变量<br />反引号包含`` 可以换行， 可以添加模板字符串
```html
<script>
   // 模板字符串
       let age = 19
       document .write (`我今年${age-10}岁了`)
       document .write(`
       哈哈哈哈
       `)
  
    </script>
```

#### ③ boolean 布尔型
表示肯定或否定时，在计算机对于的是布尔型 <br />true  false <br />蓝色

#### ④ undefined 未定义
只声明 不赋值		
#### ⑤ null 空引用
赋值的，但是内容为空<br />	
```html
<script>
  // 1. 布尔型 true false 
      console.log(true)
      console.log(false)
        // 2. undefined  只声明不赋值
       let age
       console.log(age);
        //    3. null  空
       let obj = null
       console.log(obj)
  
    </script>
```

### 3）引用数据类型
​       	- object  对象<br />			- function  函数 <br />			- array    数组

### 4）检测数据类型
typeof  数据
```html
<script>
    // 返回的什么类型  string  number Boolean null
        // null属于一个空对象
       console.log(typeof 123)
       console.log(typeof '123')
       console.log(typeof true)
       console.log(typeof false)
       console.log(typeof undefined)
       console.log(typeof null) //返回object
       let num = 10
       console.log(typeof num + '11')
       console.log(typeof (num + '11'))
       
    </script>
```
### 5）数据类型转换
表单、prompt获取的数据默认是字符串类型的。<br />就不能直接简单的进行加法运算。 
#### ① 隐式转换 
系统内部自动将数据类型进行转换 <br />1）＋号两边只要有一个是字符串，都会把另外一个转成字符串 <br />2）除了加号，其他的运算-（减号、负号）能转换成数据<br />加号作为正号解析可以转换为number 
#### ② 显式转换
1.转换为数字型 Number（ 数据） <br />只能放数字类型的字符，不能放abc，否则会返回NaN (Not a number） 

里面可以加abc，可以自动过滤只留下数字，只能识别以数字开头的<br />parseInt （转换成整数，不会四舍五入，Int要大写） <br />parseFloat (保留小数，）
```html
<script>
    // number(可以保留所有的数字，但不能掺杂其他abc)
        console.log(Number('10'))
            //    parseInt （转换成整数，不会四舍五入，Int要大写，可以掺杂abc）
        console.log(parseInt('10'))
        console.log(parseInt('10.1111 abc'))
        console.log(parseInt('10.99'))
            //    parseFloat (只保留数字，经常用于过滤px单位）
        console.log(parseFloat('10.99'))
        console.log(Number('10.99 abd')) //NaN
        console.log(parseFloat('10.99abc'))
        console.log(parseFloat('100px'))
            //    parseFloat (只能识别以数字开头的）
        console.log(parseFloat('px100px')) //NaN
       
    </script>
```
#### ③ 转换为字符型
1.String （要转换的内容）<br />2. 变量 .toString() 括号里写几进制（二进制）
```html
<script>
       console.log(String(10))
        let age = 19
        console.log(age.toString())
       
    </script>
先乘除余，后加减，有括号先算括号的，从左到右
```
# 3.流程控制
## 3.1 运算符
### 1）算术运算符
加、减、乘、除、 (+, -, *, /)<br />取模（取余）%       

经常判断作为某个数字是否被整除   

余数为0就能被整除   

```html
<script>
        console.log(4 / 2)
        console.log(4 % 2) //4除以2能不能被整除,答案0
            //    前面的数比后面小，余下的就是前面的数
        console.log(2 % 4)//2
        console.log(5 % 8)
    </script>
```
优先级：先乘除余，后加减，有括号先算括号的，从左到右

### 2）赋值运算符
1.= 将等号右边的值赋值给左边，要求左边是一个变量<br />先把右边，再给左边 <br />2. <br />累加 += <br />变量= 变量＋xx <br />-=<br />改变了变量自身的值，发生数据传递（自己传递给自己）
### 3）一元运算符
一元运算符: 仅操作一个操作数. 比如: 正负号等 <br />改变了变量自身的值，发生数据传递（自己传递给自己）<br />1）自增++ <br /> ++num <br />num++ <br />单独操作相当于num+=1 <br />2）自减-- <br />让变量的值-1 <br />经常用于计算次数

相同点<br />			不管是++或者-- 是在前还是在后,都是在原来的取值上自行增1或减1  类似于 => a += 1<br />单独使用的时候没有区别，作为运算符有区别<br />		不同点<br />			符号前置 => 先加1 再使用 (快捷记忆: ++在前 先自加) 相当于+=1<br />			符号后置 => 先使用 再加1 (快捷记忆: ++在后, 后自加)<br />	![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1652943270850-0075c26b-2a7e-4ace-83b2-a22e74e9ffda.png)



```html
<script>
  
        // 前置自增 先自加再使用
        let i = 1
        console.log(++i + 2) //答案4，i=2
            // 后置自增 先使用 再自加
        console.log(i++ + 2) //答案4，i=3
        console.log(i) //3
    </script>
```
前置自增和后置自增单独使用没有区别 <br />参与运算有区别<br />前置自增：先自加，再运算 <br />后置自增：先运算再自加 <br />后自增 num++用的更多
### 4）比较运算符
> , < , >= , <= , <br />== 值相等 <br />！=左右两边的值是否不等 <br />=== 值和类型都相等 <br />!== 左右两边是否不全等 <br />比较结果只有true或false 

在实际工作的时候判断是不是全等用===
```html
<script>
  
     console.log(3 > 5)
     console.log(5 >= 5)
    //  console.log(5 = 5) ❌ 赋值号
    console.log(5 == 5)
    // == 只要值一样就成立，不管数据类型
    console.log(5 == '5')
    // ===值和数据类型都要相等，开发常用
    console.log(5 === '5')
    </script>
```

比较运算符的特殊情况<br /> 1）字符串比较 <br />比较字符对于的ASCII码 <br />从左到右依次比较 <br />如果第一位一样再比较第二位，以此类推 <br />2）NaN  不是数字(但属于数字类型），不等于任何人，也不等于自己 <br />涉及到"NAN"的比较都是false （NaN）<br />3）不要比较小数，精读不一样 0.1+0.2 不等于 0.3 <br />4）不同数据类型比较，会进行隐式转换<br />5）如果是布尔值参与比较 布尔值会转换成数字0和1(false0,true1)
```html
<script>
  
    // &&逻辑与 一假则假
        console.log(true && true)
        console.log(false && false)
        console.log(true && false)
        // 逻辑或 || 一真全真,全假则假
        console.log(true || false)
        console.log(false || false)

        // 逻辑非 ！取反
        console.log(!true)
        console.log(!false)
    </script>
```
### 5）逻辑运算符
逻辑运算符用来解决多重条件判断 <br />1） && 逻辑与 并且 <br />符号两边都为true ，结果才为true （一假则假） <br />2） || 逻辑或 <br />或者，符号两边有一个true就为true（一真则真） <br />3） ！ 逻辑非 取反 （也是一个一元运算符）<br />true变false，false变true （真变假，假变真）


逻辑运算符里的短路 <br />只存在&&和||中，当满足一定条件会让右边代码不执行<br /> && 左边为false就短路<br /> || 左边为true就短路 <br />原因：通过左边能得到整个式子的结果，因此没必要再判断右边 <br />运算结果，短路后直接返回前面的值，后面不执行，不短路以后面的为准。 <br />有5个值当false来看 false、数字0，' '空字符串，undefined，null，其余是真的
### 6）运算符优先级
1.小括号 <br />2.一元运算符 ++ -- ！ （取反）<br />3.算术运算符 先乘除余再加减 <br />4.关系运算符 大于小于 大于等于 <br />5.相等运算符 === ！== <br />6.逻辑运算符 先&& 后|| <br />7.赋值运算符 = <br />8.逗号运算符，

## 3.2 表达式
### 1）表达式和语句
表达式<br />		表达式是一组代码的集合，JavaScript解释器会将其计算出一个结果<br />			x = 7<br />			3 + 4<br />			num++<br />	语句<br />		js 整句或命令，js 语句是以分号结束（可以省略）<br />			if 条件语句<br />			for 循环语句<br />	区别<br />		达式计算出一个值，但语句用来自行以使某件事发生。<br />			表达式  3 + 4 <br />			语句  alert()  弹出对话框

### 2）语句分类
   顺序语句<br />	分支语句<br />	循环语句

### 3）分支语句
#### ①if分支
##### 	单条分支
	if（条件）{ 满足条件要执行的代码 }

只有一行函数体代码，大括号可以省略<br />if（条件）满足条件要执行的代码 

如果条件是true，进入大括号执行 <br />小括号内的结果若不是布尔类型，会发生隐式转换为布尔类型<br />这6种 布尔型为false ：<br />// false 0 ‘’ undefined null NaN<br />其余 的都是true
##### 	双分支
	if（条件）{ 满足条件要执行的代码 } else { 不满足条件执行的代码 } 

##### 	多条分支
if（条件）{ 满足条件要执行的代码 } <br />else if（条件2） { 满足条件执行的代码 }<br />else if（条件3） { 满足条件执行的代码 } <br />else { 不满足条件执行的代码}
#### ② 三元运算符/三元表达式
if else的简便写法 <br />条件？满足条件执行的代码（表达式）：不满足条件执行的代码 （表达式）<br />作用：一般用来取值，有返回值，可以拿变量接
#### ③ switch case
	出现定值判断使用

```html
 <script>
       switch (数据){
           case 值1:
              代码1
               break
           case 值2:
               代码 2
               break
           case 值3:
               代码
               break
            default:
               代码n
              
       }

    </script>
```
找到跟小括号里数据全等===的case，并执行里面的代码 <br />如果没全等===，则执行default里的代码（不一定要有default） 

特点说明<br />		1. switch case语句一般用于等值判断,不适合于区间判断<br />		2. switch case比较的值全等 ===<br />		3. switch case一般需要配合break关键字使用 没有break会造成case穿透

#### ④ 分支语句的综合
if 分支<br />		 使用的最多的分支语句  任何情况下都可以通用<br />	三元运算<br />		可以简单理解为两条分支的简写形式,一些简单的两条分支可以使用三元运算符代替<br />		相较正常的两条分支语句来说多了一个返回值<br />	switch case语句<br />		当出现了定值判断的时候可以使用<br />	多分支语句和switch的区别<br />		如果值比较精确用switch ，效率更高<br />		如果有范围的判断，用多分支语句

### 4）循环语句
断点调试 打断点要刷新 
#### ① while 循环 
while （终止条件(区间））{ 要重复执行的代码 变量变化量 } 
```html
 <script>
        // 循环必须有3要素
       
       
        let i = 1 // 变量的起始值
        
        while (i <= 3) {  // 终止条件
            document .write('hahah <br>')
            i++ //变量变化量

        }
    </script>
```
##### 循环三要素 
1.变量起始值 <br />2.终止条件 <br />3.变量变化量 （用自增 或者 自减） 

##### continue和break
continue 结束本次循环，继续下一次循环
```html
 <script>
         // 我们要打印吃包子
        let i = 1
        while (i <= 6) {
            if (i === 3) {
                i++ //这行不能省略，三要素
                continue       
            }
            document.write(`我要吃第${i} 个包子 <br>`)
            i++
        }
    </script>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1653029350521-61ccbbd6-f9eb-4623-8b79-395186a1869f.png)

break 跳出所在的循环，（全部终止）
```html
 <script>
         // 我们要打印吃包子
        let i = 1
        while (i <= 6) {
            if (i === 3) 
               break    //直接退出不需要任何操作    
            }
            document.write(`我要吃第${i} 个包子 <br>`)
            i++
        }
    </script>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1653029386694-0697bad5-4c73-434c-935f-a244907d1f6d.png)
#### ② for循环
for 循环 <br />把声明起始值，循环条件、变化值写到一起 <br />for（起始条件；循环条件；变化值）{ 循环语句 } <br />for循环的最大价值：循环数组(遍历） <br />可以通过arr.length知道数组里有几个元素 <br />i<= arr. length -1<br />i< arr.length

##### continue和break
```html
 <script>
        for (let i = 1; i < 6; i++) {
            if (i === 2) {
                continue //不需要再加别的操作，三要素在开头
                // break
            }
            document.write(i)
        }
    </script>
```
基本和while一致<br />		1. break: 一般用于结果已经得到, 后续的循环不需要的时候可以使用<br />		2. continue: 一般用于排除或者跳过某一个选项的时候, 可以使用continue
##### 双层for循环嵌套
for （外部声明记录循环次数的变量；循环条件；变化值）{ <br />for （内部声明记录循环次数的变量；循环条件；变化值）{ } <br />} <br />外面循环执行一次，里面循环执行全部

```html
 <script>
     // 外层打印几行
        for (let i = 1; i <= 5; i++) {
            // 里层打印几个星星
            for (let j = 1; j <= i; j++) {
                document.write('★')
            }
            document.write('<br>')
        }
    </script>
    </script>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1653037701331-23735760-f1e8-47fb-88d2-49eb7e342b63.png)
#### ③循环的小结
 for循环: 当如果明确了循环的次数的时候推荐使用for循环<br />while循环: 当不明确循环的次数的时候推荐使用while循环

# 4. 数组
数组的本质是数据集合<br />数组里可以放任何类型数据， 对象、数组
## 4.1 创建数组
字面量：let arr=[]<br />构造函数 new Array()

## 4.2 数组的使用
	数组本质是数据集合,使用无非就是增删改查
### 1）查：查询、访问、得到
		数组[下标]
### 2） 改：重新赋值
数组[下标] = 新值<br />不能直接arr=

### 3） 增：添加新的数据
#### arr.push(新增的内容)
将一个或多个元素添加到数组的末尾，并返回该数组的新长度<br /> arr.push( 元素1。。。元素n）

#### arr.unshift(新增的内容)
将一个或多个元素添加到数组的开头，并返回数组的最新长度
```html
 <script>
        let arr = ['red', 'green']
            // 把 blue 放到 arr 的后面
            // arr.push('blue')

        // console.log(arr.push('blue'))//3
        arr.push('blue', 1)//把元素放到arr后面
        console.log(arr.push('blue', 1))//4
        console.log(arr.length)//4
   
   
        arr.unshift(2, 3)//把元素放到arr前面
        console.log(arr.unshift(2, 3))//6
        console.log(arr.length)//6
    </script>
```
### 4）删
#### arr.pop()
从数组中删除最后一个元素，并返回该元素的值 <br />括号里不要加任何东西

#### arr.shift()
从数组中删除第1个元素，并返回该元素的值 <br />括号里不要加任何东西

#### arr .splice (start, deleteCount) 
start指定位置开始（从0计数） <br />deleteCount 删几个 <br />如果不写deletcount，就是从指定位置开始，把后面的全部删除<br />返回被删除的值
```html
 <script>
       // let arr = ['red', 'green', 'blue']
        // pop删除最后一个元素
        // arr.pop()
        
        // 返回的是被删除的元素
        // console.log(arr.pop())
        // arr.shift()
       
        // shift删除第一个元素
        // console.log(arr.shift())
        // console.log(arr)


        let arr = ['red', 'green', 'blue']
        // splice(从哪里开始删（下标号，从0开始），删除几个元素)
        // 返回的是被删除的值
        // arr.splice(1, 1)
        // console.log(arr.splice(1, 2))

        // 不写deletecount就是把起始值后面都删掉
        arr.splice(1)
        console.log(arr)
    </script>
```
## 4.3 数组遍历
### 1）for循环
for （let i=0，i<数组.length,i++){<br />依次对数组进行操作}
### 2）forEach（）方法
数组.forEach(function(item,index,o){<br />依次对数组进行操作<br />item——数组的每个对象<br />index——数组每个对象对应的索引<br />o——当前这个数组})
# 5. 函数
函数：function 被设计为执行特定任务的代码块 <br />作用：精简代码方便复用，提高开放效率，随时调用，随时执行，可重复调用 
## 5.1 函数声明和调用
声明语法：function 函数名（）{ 函数体 } <br />调用语法： 函数名（） <br />小括号里不加东西

函数命名规范： <br />1.和变量命名基本一致 <br />2.尽量小驼峰 <br />3.前缀应该为动词 <br />can 可执行某个动作 <br />has 判断是否含有某个值 <br />is 判断是否为某个值 <br />get 获取某个值 <br />set 设置某个值 <br />load 加载某些数据
## 5.2 函数传参
作用，提高了函数的灵活性 <br />1.声明 function 函数名（形参，逗号隔开）{ 函数体} <br />2.调用 函数名（实参）{ 函数体} <br />3. 形参作用: 本质上就是在函数内部声明变量<br />4. 实参作用: 给形参赋值<br />5. 我们曾经使用过的 alert('打印'), parseInt('11'), Number('11') 本质上都是函数调用的传参

### 参数逻辑中断
```html
 <script>
       // x y函数内变量
        // 如果一个变量没有赋值，则默认为undefined
        // undefined +'' 为 undefined
        //undefined+其他的值都是NaN

        function getSum(x, y) {
             x = x || 0
             y = y || 0
            document.write(x + y)

        }

        getSum() //没有给xy传参，xy为undefined
    </script>
```
// undefined +''(字符串） 为 undefined<br />//undefined+其他的值都是NaN


## 5.3 函数返回值
把处理结果返回给调用者<br />1）return会立即结束，下一行的代码不再执行，所以不要换行写 <br />2）函数默认没有返回值，返回值是undefined<br />3）return后面什么都不写，返回值也是undefined

```html
 <script>
        function fn() {
           return
           alert(11) //写在return后面不执行
       }
         fn()
   
   
        function fun() {
            return
        }
        let re = fun()
        console.log(re) //undefined
    </script>
```
使用过的返回值<br />	let result = prompt('请输入你的年龄?');		 //返回值：年龄<br />	let result2 = confirm('你确定要删除这条记录么?')  //返回值：true、false<br />	let result3 = parseInt('111');  //返回值：数字<br />	// 函数的返回值不是必须的, 比如: alert() <br />let result4 = alert('弹出一个内容');  //返回值：undefined

### return多个返回值
return只能返回一个值，如果要返回多个值用数组<br />return [数据1，数据2]
```html
 <script>
      function fn(x, y) {
            let jia = x + y
            let jian = x - y
            // return jia, jian 结果值返回了 jian 因为return只能返回一个值
            return [jia, jian]
        }
        let re = fn(1, 2)   //  [3, -1]
        document.write(`相加之后的结果是：${re[0]},相减之后的结果是: ${re[1]} `)
    </script>
```

细节补充<br />1.两个相同的函数后面的会覆盖前面的函数<br />2.在Javascript中 实参的个数和形参的个数可以不一致<br />		如果形参过多 会自动填上undefined<br />		如果实参过多 那么多余的实参会被忽略 (函数内部有一个arguments,里面装着所有的实参)<br />3.实参可以是变量
```html
 <script>
    let num1 = +prompt('请输入一个数：')
        let num2 = +prompt('请输入另一个数：')
        function getMax (x,y){
        //   三元表达式
       return  x > y ? x : y

            // if (x > y){
            //     return x
            // } else {
            //     return y
            // }

        }
    //    实参可以放变量
      let max = getMax (num1,num2)
      document.write(max)
    </script>
```
	函数一旦碰到return就不会在往下执行了  函数的结束用return<br />		1. 思考: break的结束和return结束有什么区别 ?
## 5.4 作用域
（可用性的代码范围） <br />1.全局作用域script <br />2.局部作用域  函数内部（函数作用域 ）<br />3.块级作用域{} if、for里
### 1）变量种类
#### 	①全局变量
		 在函数外部let 的变量  => 全局变量在任何区域都可以访问和修改
```html
 <script>
    // 1. 全局变量  全局能用
        let num = 10
        console.log(num)
        function fn() {
            console.log(num)
        }
        fn()
        if (true) {
            console.log(num)
        }
    </script>
```
#### 	②局部变量
		在函数内部let 的变量  => 局部变量只能在当前函数内部访问和修改  
```html
 <script>
  // 2. 在局部作用域下，变量是 局部变量
        // 函数内的变量，只能给内部使用，函数外面不能使用
        function fn() {

            let num = 10
            console.log(num)
            function fn1() {
                console.log(num)
                let num2 = 20
            }
            fn1()
            // console.log(num2)  num2 is not defined
        }
        fn()
        console.log(num) // num is not defined

    </script>
```
函数里套函数，大的作用域包含小的作用域，小的作用域不包含大的作用域。<br /> 函数内的变量只能给内部使用，外部不能使用。
```html
 <script>
   function fn(x, y) {
            // x 和 y 可以看做是 局部变量
            document.write(x + y)
        }
        fn(1, 2)
        console.log(x) //错误了
    </script>
```
####       ③块级变量
		let定义的变量,只能在块作用域里访问,不能跨块访问,也不能跨函数访问
```html
 <script>
    // 3. 块级变量  
        if (true) {
            let num = 10
        }
        console.log(num) //undefined
        for (let i = 0; i < 5; i++) {
            console.log(i)
        }
        console.log(i) //undefined

    </script>
```
大括号里面的变量，大括号外面不能使用
### 2）变量特殊情况
如果函数内部或块级作用域内部，变量直接赋值，没有声明，当全局变量看，（强烈不推荐）<br /> num = 10 <br />函数形参可以理解为局部变量 <br />global全局 <br />local 局部<br />block块级 
### 3）作用域链
就近原则 先看自己局部内部的作用域，然后再往上看

## 5.5 具名函数和匿名函数
### 1） 具名函数
声明 function fn（）{} <br />调用 fn （）

### 2）匿名函数
 function() {} <br />函数表达式：let fn（变量） = function（）{ 函数体 } <br />调用 变量名 （） 

参数和具名函数一样

### 3） 立即执行函数
立即执行函数：无需调用 <br />场景：避免变量污染<br />*多个立即执行行数之前要加上分号，用；隔开，不然会报错
```html
 <script>
   let num = 10
           ; (function () {
                // 防止变量污染
                let num = 20
            })();
    (function() {
            console.log(222)
        })()

    </script>
```
 let fn = function() {} <br />fn() <br />(function () {} )() <br />第一个小括号放的是形参 <br />第二个小括号放的是实参
```html
 <script>
    (function (x, y) {
            console.log(x + y)
        })(1, 2)

    </script>
```
立即执行行数也可以加函数名 <br />let fn = function fun () {} <br />fn() <br />(function fn () {} () ） 


## 5.6 函数传参问题
### 1） 实参个数少于形参 undefined 
// undefined +''(字符串） 为 undefined<br />//undefined+其他的值都是NaN
```html
 <script>
    function fn(x, y) {
            // x = 1 
            // y = undefined
            // 1 + undefined  =  NaN
            console.log(x + y)
        }
        fn(1) //NaN
        fn(1,2,3)  //3, 多的参数被忽略 
    </script>
```

###  2）实参个数大于形参，多的被忽略 
### 3） fn（）arguments 动态参数
arguments是一个伪数组 <br />在函数内，只在函数内有效容通过伪数组形式调用实参 <br />区别，没有pop，push，shift等方法
```html
 <script>
   function fn() {
            // arguments 函数内有效   表现形式 伪数组 
            // 伪数组 比真数组 少了一些 pop()  push()  等方法 
            console.log(arguments) //  [1,2,3]
            let sum = 0
            for (let i = 0; i < arguments.length; i++) {
                sum += arguments[i]
            }
            console.log(sum)
        }

        fn(1, 2, 3)
    </script>
```
### 4）形参初始值
函数传参 function fn（x= 0， y=0) {}<br />fn() 调用的时候，会有内部判断是否有参数传递过来，<br />没有参数则执行x= 0，有参数则执行实参
```html
 <script>
   逻辑中断
  // function fn(x, y) {
        //     x = x || 0
        //     y = y || 0
        //     console.log(x + y)
        // }
        // fn(1, 2)
        // fn()
   
   
   
   函数初始值
        // x 和 y 可以看做是 函数内部的局部变量
        // 调用的时候会有个内部判断是否有参数传递过来
        // 没有参数 则 执行 x = 0
        // 有参数，则执行 实参赋值
        function fn(x = 0, y = 0) {
            console.log(x + y)
        }
        fn() //0
        fn(3, 5)//8
    </script>
```

# 6. 对象
什么是对象? 为什么需要对象?<br />	何为对象：万物皆对象,对现实事物的描述。客观世界中的具体的实体都是对象 如一个人,一个气球,一辆汽车,咱们的 班主任等.<br />	需求: 如何在JS中存储班主任这个对象的信息 ?<br />		- 静态特征 (姓名, 年龄, 身高, 性别, 爱好) => 可以使用数字, 字符串, 数组, 布尔类型等表示<br />		- 动态行为 (点名, 唱, 跳, rap) => 使用函数表示

对象的基本语法介绍<br />	在Js中, 对象就是一组无序的键值对的集合<br />	说明<br />		1. 我们把冒号左边的内容称之为属性, 右边称之为值, 成对出现, 故称之为键值对<br />		2. 当右边的值为函数的时候, 我们更喜欢将这个属性称之为方法<br />		3. 对象本质上也是一种数据集合, 对比数组来说它里面装的都是不同类型的数据, 并且有对应的属性提示数据的含义<br />	
## 6.1 声明对象
let 对象名 = {  <br />属性名：属性值，<br /> uname: 'Andy '， <br />方法名：函数<br />最后一个属性不用加逗号 <br /> }
## 6.2 对象使用
### 1）查：
#### ①属性访问 
1.对象名.属性 <br />2.对象名['属性名'] <br />对比点语法的相同点和不同点<br />	1. 都可以访问对象的属性 对象名.属性名 === 对象名['属性名']<br />	2. []语法里面的值如果不添加引号 默认会当成变量解析<br />	3. 没有必要的时候直接使用点语法, 在需要解析变量的时候使用 [] 语法<br />*方法名也可以当成属性访问，得到的值是一个函数，不会执行
#### ②方法访问
对象的方法是一个匿名函数  <br />方法名： function(形参) { 函数体 } <br />访问对象方法 <br />对象名.方法名（实参

```html
 <script>
  let goods ={

        // 属性名只在对象里有效
          name: '小米小米10 青春版',
          num: 100012816024,
          weight: '0.55kg',
          address:'中国大陆',
          sayHi: function (){
              console.log('hi~')
          }, 
        //   一定要加逗号隔开
          movie: function (n){
              console.log(n)
          }
      }

    //   属性访问
    //     1.对象名.属性
      console.log(goods.name)
      console.log(goods.weight)

    //   2.对象名['属性名']
      console.log(goods['num'])
      console.log(goods['address'])

    //   方法访问
    //   对象名.方法名（ 实参）
    goods.sayHi()
    goods.movie('无间道')


        goods.price = 3999
        console.log(goods.sayHi) //  ƒ () {console.log('hi~') }
        console.log(goods['sayHi']) //  ƒ () {console.log('hi~') }
    </script>
```
### 2）增/改 ：
对象.新属性=新值 <br />对象['新属性']=新值 <br />对象.方法 = function （）{}

### 3）删：
delete 对象.属性
```html
 <script>
   let obj = {
            uname: '小明',
            age: 18
        }

        console.log(obj.age)
            // 修改：对象.属性=新值
        obj.age = 81
        console.log(obj)

        // 新增一个属性
        // 对象.新属性=新值
        obj.sex = '男'
        obj['hobby'] = '足球'
        console.log(obj)

        // 新增方法 对象.方法 = function （）{}
        obj.sing = function() {
            console.log('恭喜发财')
        }
        console.log(obj)

        // 删除 delete 对象.属性名
        delete obj.hobby
        console.log(obj)
        delete obj.sing
        console.log(obj)


     
    </script>
```

## 6.3 对象遍历
for (let k in obj){ <br />console.log(obj[k]) <br />k不要加引号        }
```html
 <script>
        let obj = {
            uname: '小明',
            age: 18,
            sex: '男'
        }

        // for in 语法 遍历对象   
        // for (let k in 对象)
        // 重点
        // k/key value 变量
       for (let k in obj){
        //    console.log(k) k是属性名 k==='uname'==='age'==='sex'
        // console.log(obj.k) obj里的k属性 （但是obj里没有）

        console.log(obj[k])
        // obj[k]===obj['uname']
       }
    </script>
```
 k是变量  ，属性名  <br />k==='uname'==='age'==='sex' <br />obj[k]===obj['uname']
## 6.4  数组和对象
数组里可以放任何类型数据， 对象、数组<br />用for循环遍历数组，得到数组里每个对象的值
```html
 <script>
        // 数组 里面可以放任何的数据类型
        // let arr = [1, 'pink', true, undefined, null, {}, []]
        // console.log(arr)
        // 数组对象
        let students = [
            { name: '小明', age: 18, gender: '男', hometown: '河北省' },
            { name: '小红', age: 19, gender: '女', hometown: '河南省' },
            { name: '小刚', age: 17, gender: '男', hometown: '山西省' },
            { name: '小丽', age: 18, gender: '女', hometown: '山东省' }
        ]
        // 遍历数组
        for (let i = 0; i < students.length; i++){
            console.log(students[i])//得到数组里每个对象
            console.log(students[i].name)//得到数组里每个对象的姓名
           console.log(students[i]['hometwon'])//得到数组里每个对象的家乡
   
        }
       

    </script>
```
## 6.5 数学内置对象
### 1）Math.min(x,y) 求最小值
### 2）Math.max(x,y)求最大值
Math.abs(x-y)求最绝对值

```html
 <script>
        console.log(Math.PI) //圆周率 π
        console.log(Math.random()) //返回0-1随机小数 包括0，不包含1
        console.log(Math.ceil(1.6)) //返回 2，向上取整
        console.log(Math.floor(1.6)) //返回 1，向下取整
        // console.log(parseInt(1.6))
        console.log(Math.round(1.6)) //返回 2，就近取整，往大取整）
        console.log(Math.round(-1.5))  //返回 -1

        // 求最大值、最小值
        console.log(Math.max(1,5,9,45))
        console.log(Math.min(1,5,9,45))

    </script>
```
### 3）封装随机数函数
生成任意范围随机数 Math.floor(Math.random()*(M-N+1))+N
```html
 <script>
        //   封装随机数
    function getRandom (min,max){
        return Math.floor(Math.random()* (max - min + 1) +min )
         
    }
    let random = getRandom (1,100)
    console.log(random)

    </script>
```
# 7. 栈和堆
栈：简单数据类型（值类型      <br />引用数据类型的地址 


堆：引用数据类型（对象、数组
