# 1. web api
## 1.1 作用：
用js操作html和浏览器 
## 1.2 分类：
dom（文档对象模型） ——操作html和css<br />bom（浏览器对象类型）——操作浏览器<br /> 
# 2.DOM（Document Object Model）

文档对象模型<br />dom是浏览器提供的一套专门用来操作网页内容的功能：实现网页特效和用户交互
## 2.1 DOM树

HTML DOM 定义了访问和操作 HTML 文档的标准方法<br />DOM 以树结构表达 HTML 文档<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1653355679097-240ca7e8-b819-4011-bfcf-81a4baa62198.png)

## 2.2 DOM对象
浏览器根据html标签生成的JS对象<br />	所有的标签属性都可以在这个对象上面找到<br />	修改这个对象的属性会自动映射到标签身上

document是dom里的一个对象 <br />document.write（）对象里的方法，网页所有内容都在document里。

## 2.3 获取DOM对象
### 	1）document.querySelector（‘css选择器’）
参数是字符串，一定要加引号，返回css匹配的【第一个元素】<br />可以直接操作
### 	2）document.querySelectorAll（‘css选择器’）
参数是字符串，一定要加引号 <br />返回css匹配的【Nodelist对象合集】，<br />可以通过遍历的方式给里面的元素做修改，用for循环，也可以用forEach <br />得到一个伪数组，有长度有索引号，但是没有pop，push等数组方法
### 	3）其他
document.getElementById()<br />document.getElementsByTagName()

```html
<body>
    <div>我是一个盒子</div>
    <div>我是第二个盒子</div>
    <div class="three">我是第三个盒子</div>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
    </ul>
    <span>就1个</span>
    <script>
        // 1. js 获取 第一个元素 
        // let div = document.querySelector('div')
        // console.log(div)  只能获取到第一个
      
      
        // let div = document.querySelector('.three')
        // let li = document.querySelector('ul li:last-child')
        // console.log(li) css选择器能获取到唯一的那个
      
        // 2. 获取多个元素  伪数组
        let lis = document.querySelectorAll('ul li')
        console.log(lis) //[div, div, div]
            // 通过遍历的方式，获得里面的每一个dom对象（元素）
      forEach遍历
      lis.forEach(function(item, index) {
            console.log(item, index);
        })

      for循环遍历
        // for (let i = 0; i < lis.length; i++) {
        //     console.log(lis[i])
        // }
      
        // let span = document.querySelectorAll('span')
        // console.log(span) 一个只有一个对象的伪数组
    </script>
</body>
```
## 2.4 设置/修改元素内容
DOM对象都是根据标签生成的,所以操作标签,本质上就是操作DOM对象.<br />		就是操作对象使用的点语法<br />1.document.write () 只能将文本内容追加到</body>前面的位置，可以解析标签， <br />2.innertext 属性(里面的文字） <br />键值对<br />innertext = ‘’<br />将文本内容添加、更新到任意标签位置，不能解析标签 <br />3.innerHTML 属性 <br />键值对<br />innertext = ‘’<br />将文本内容添加、更新到任意标签位置，可以解析标签<br />	使用:  不明确数据的安全性的情况下, 使用innerText

```html
<body>
    <div>
        粉红色的回忆
    </div>

    <script>
        // 1. 获取标签(元素)
        let box = document.querySelector('div')
        console.log(box.innerText)// 粉红色

        // 2. 修改标签（元素）内容  box是对象   innerText 属性
        // 对象.属性  = 值   不识别标签
        // box.innerText = '有点意思~'
        // box.innerText = '<strong>有点意思~</strong>'
        // 3. innerHTML解析标签
        box.innerHTML = '<strong>有点意思~</strong>'
        console.log(box.innerHTML)//
    </script>
</body>
```
要区分模板字符串的区别<br />js不用写结构，直接内部填充

## 2.5 设置/修改元素属性
### 1）常用属性
href、title、src<br />元素.src =' '
```html
<body>
    <img src="./images/1.webp" alt="">
    <script>
        // 1. 获取元素 图片
        let pic = document.querySelector('img')
        // 2. 修改元素属性  src  对象.属性 = 值
        pic.src = './images/3.webp'
        pic.title = '我是pink老师'
    </script>
</body>
```
### 2）元素样式属性
#### 	①  style操作css
​	每一个DOM对象都有一个style属性,style属性的值是一个对象，里面存储了所有行内样式对应的键值对。<br />		如果样式的名字带了-，比如background-color,到了style对象中，变成了驼峰命名法 backgroundColor（因为-在js中-会被解析成减号）<br />                对象.style.样式属性 = ' 值 ' （不要忘记加单位）<br />		style属性只能获取和设置行内样式，在类样式中定义的样式通过style获取不到。

```html
<body>
     <div> </div>
    <script>
        // 1. 获取元素
        let box = document.querySelector('div')
        // 2. 改变背景颜色 样式  style 
        box.style.backgroundColor = 'hotpink'
        box.style.width = '400px'
        box.style.marginTop = '100px'

    </script>
</body>
```

#### 	②操作类名(className)
由于class是关键字, 所以使用className去代替<br />className是使用新值换旧值, 如果需要添加一个类,需要保留之前的类名<br />元素.className ='类名'<br />只保留最后的类，之前的会被覆盖

```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
        
        .active {
            width: 300px;
            height: 300px;
            background-color: hotpink;
            margin-left: 100px;
        }
        
        .one {
            border: 1px solid #000;
        }
    </style>
</head>

<body>
    <div class="one"></div>
    <script>
        // 1.获取元素
        // let box = document.querySelector('css选择器')
        let box = document.querySelector('div')
            // 2 设置样式div
            // box.style.width = '300px'
            // box.style.height = '300px'
            // box.style.backgroundColor = 'hotpink'
            // box.style.marginLeft = '100px'
        box.className = 'active' //.one 的边框线被覆盖了
        box.className = 'one active'//如果想要叠加样式，要把之前 的类名 带上
    </script>
</body>
```

#### 	③ classList
作用，className容易覆盖以前的类名<br />classList是一个对象
##### 添加：
元素.classList.add('类名 1'，‘类名2’)
##### 删除：
元素.classList.remove('类名 ')
##### 切换：
元素.classList.toggle('类名 ') <br />原来有，切换没有 <br />原来没有，切换有
##### 包含：
元素.classList.contains('类名 ') <br />有返回true，没有返回false

```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 200px;
            height: 200px;
            background-color: pink;
        }
        
        .active {
            width: 300px;
            height: 300px;
            background-color: hotpink;
            margin-left: 100px;
        }
        
        .one {
            border: 1px solid #000;
        }
    </style>
</head>

<body>
    <div class="one"></div>
    <script>
        // 1.获取元素
        // let box = document.querySelector('css选择器')
        let box = document.querySelector('div')

        // add是个方法 添加  追加
        box.classList.add('active') //原来的样式+active
            // remove() 移除 类
        box.classList.remove('one') //减去这个类
            // 切换类
        box.classList.toggle('one') //原来没有就加上，原来有就去掉
    </script>
</body>
```
#### 	④对比className和style、classList的区别
修改大量样式的更方便<br />修改不多样式的时候方便<br />classList 是追加和删除不影响以前类名

### 3) 表单属性
正常的有属性**有取值**的 跟其他的标签属性没有任何区别<br />获取: DOM对象.属性名<br />设置: DOM对象.属性名 = 新值<br />表单.value ='用户名' <br />表单.type='password' （表单数据类型）

```html
<body>
    <input type="text" value="请输入">
    <button disabled>按钮</button>  /* 默认禁用按钮*/
    <input type="checkbox" name="" id="" class="agree">
    <script>
        // 1. 获取元素
        let input = document.querySelector('input')
            // 2. 取值或者设置值  得到input里面的值可以用 value
            // console.log(input.value)
        input.value = '小米手机'
        input.type = 'password' //修改表单数据类型

        // 2. 启用按钮
        let btn = document.querySelector('button')
            // disabled 不可用   =  false  这样可以让按钮启用
        btn.disabled = false
            // 3. 勾选复选框
        let checkbox = document.querySelector('.agree')
        checkbox.checked = true  //自动勾选
    </script>
</body>
```
表单属性中添加就有效果,移除就没有效果,一律使用布尔值表示 如果为true 代表添加了该属性 如果是false 代表移除了该属性<br />常见表单属性<br />value、disabled、checked、selected

### 4）元素的大小和位置
#### ① scroll家族
1.获取元素内容总宽高（不含滚动条） ，包括padding<br />2.获取位置 获取（整个元素）被卷去的头部 scrollTop,和scrollLeft <br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1653981907893-63115a14-2482-4d58-85a9-d145689fae7a.png)<br />值是数字型 ，不带单位<br />这两个数是可修改的，不要带单位 <br />html的元素 document.documentElement<br />document.documentElement.scrollTop = 500

#### ② offset家族
获取宽高，包含元素自身宽高、padding、border <br />获取位置 <br />1.获取元素距离自己最近一级【定位父级】元素的左、上距离 <br />2.如果父级没有定位，以文档左上角为准 （offsetLeft和offsetTop是只读属性）

#### ③ client家族
当前可视区域,不包含滚动条和边框clientWidth，clientHeight<br />获取位置 clientLeft、clientTop <br />可视区到盒子边框的距离=边框宽度，没有边框=0，只读属性

#### ④ 三大家族宽高对比
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1653983813445-efd24c42-ba94-44bf-a429-42d15fe10b36.png)


# 3. DOM节点
## 3.1 DOM节点类型和作用
dom树里每一个内容都称之为节点 <br />节点类型 <br />1.元素节点（所有的标签，body、div）html是根节点<br />2.属性节点：所有的属性 <br />3.文本节点：所有的文本 <br />【重要】元素节点作用  更好理清标签元素之间的关系

## 3.2 DOM节点操作
### 1）查找节点
#### ①父节点
parentNode属性 <br />返回最近一级的父节点，找不到返回为null <br />子元素.parentNode 
```html
<body>
    <div class="box">爷爷
        <div class="father">爸爸
            <div class="son">儿子</div>
        </div>
    </div>


    <script>
        let son = document.querySelector('.son')
            // 找爸爸
            // console.log(son.parentNode)
        son.parentNode.innerText = 'pink' //最近一级的父元素，再上一级的获取不到
    </script>
</body>
```
#### ②子节点
父元素.children <br />仅获取所有元素节点 返回的还是一个伪数组HtmlCollection对象<br />伪数组遍历：只能for循环，不能用forEach<br />可以转为真数组Array.from(伪数组)，用forEach

父元素.childrenNodes，返回NodeList对象，多了节点
```html
<body>
    <button>点击</button>
    <ul>
        <li>我是孩纸</li>
        <li>我是孩纸</li>
        <li>我是孩纸</li>
        <li>我是孩纸</li>
        <li>我是孩纸</li>
        <li>我是孩纸</li>
    </ul>
    <script>
        let btn = document.querySelector('button')
        let ul = document.querySelector('ul')

        btn.addEventListener('click', function() {
            console.log(ul.children)
                // 返回htmlCollection对象

            for (let i = 0; i < ul.children.length; i++) {
                ul.children[i].style.color = 'red'
            }
        })
        ul.children[0].style.color = 'green'
            // console.log(ul.childNodes) 返回nodeList对象
    </script>
</body>
```
#### ③兄弟节点 
nextElementSibling（下一个兄弟节点）<br />previousElementSibling（上一个兄弟节点）
```html
<body>
    <button>点击</button>
    <ul>
        <li>第1个</li>
        <li class="two">第2个</li>
        <li>第3个</li>
        <li>第4个</li>
    </ul>
    <script>
        let btn = document.querySelector('button')
        let two = document.querySelector('.two')
        btn.addEventListener('click', function () {
            // two.style.color = 'red'
            two.nextElementSibling.style.color = 'red'
            two.previousElementSibling.style.color = 'red'
        })
    </script>
</body>
```
### 2）增加节点
#### ①创建一个新的节点 
document.createElement('标签名')有引号 <br />只能写元素标签名，不能再写其他类名

#### ②把创建新的节点放入到指定的元素内部 
插入到父元素里最后一个子元素 <br />父元素.appendChild（子元素）

插入到某个元素前面 <br />父元素.insertBefore(要插入的元素，在哪个元素前面） <br />每次放在最前面就是插入数组【0】的前面<br />追加的节点可以是新创建的 也可以是页面上已经存在 (移动)

```html
<body>
    <ul>
        <li>我是大毛</li>
        <li>我是二毛</li>
    </ul>
    <script>
        // 1. 创建新的标签节点
        let ul = document.querySelector('ul')
        let li = document.createElement('li')

        console.log(li);
        li.innerHTML = '我是xiao ming'
            // 2. 追加节点  父元素.appendChild(子元素) 后面追加
            ul.appendChild(li)
            // 3. 追加节点  父元素.insertBefore(子元素， 放到那个元素的前面)   
        ul.insertBefore(li, ul.children[0])
       // 同一个元素增加两次，第二次生效，叠加
       ul.insertBefore(ul.children[1], ul.children[0])//可以移动原本已经存在的节点
    </script>
</body>

```
### 3）克隆节点
元素.cloneNode(布尔值） <br />true 代表包含后代节点一起克隆 <br />false，克隆时不包含后代节点，默认为false
```html

<body>
    <ul>
        <li>我是内容11111</li>
    </ul>
    <script>
        let ul = document.querySelector('ul')
            // 括号为空则默认为false 如果是false则不克隆后代节点
            // 如果是true则克隆后代节点
        let newUl = ul.cloneNode(true)
        document.body.appendChild(newUl)
    </script>
</body>
```
用于需要创建一个复杂的标签<br />前提: 页面上有一个模板节点

### 4）删除节点
必须通过父元素删除 <br />父元素.removeChild(要删除的元素） <br />*如果不存在父子关系则删除不成功 <br />*删除和display有区别，隐藏还是存在，删除则从html中删除节点
```html

<body>
     <button>点击</button>
    <ul>
        <li>我是内容11111</li>
    </ul>
    <script>
        // 需求，点击按钮，删除小li
        let btn = document.querySelector('button')
        let ul = document.querySelector('ul')
        btn.addEventListener('click', function () {
            // 删除的语法 父元素.removeChild(子元素)
            ul.removeChild(ul.children[0])
        })
    </script>
</body>
```

# 4. 事件
编程时系统发生的动作或者发生的事情，比如用户在网页上单击一个按钮
## 4.1 事件监听 
（绑定事件、注册事件、事件侦听） <br />让程序检测是否有事件发生，一旦有事件触发，立即调用一个函数做出响应
### 1）事件三要素
1.事件源：哪个dom被事件触发了，要获取dom元素 <br />2.用什么方式触发，比如鼠标单击click，鼠标经过mouseover <br />3.事件调用的函数：要做什么事,点击之后再去执行，每次点击都会执行一次
### 2）语法
元素.addEventListener（'事件'，要执行的函数）
### 3）事件监听版本
1.dom lo 事件源.on 事件 = function（）{} <br />2.dom l2 事件源.addEventListener(‘事件’，事件处理函数）<br />拓展阅读<br />	DOM L0 ：是 DOM 的发展的第一个版本；   L：level<br />	DOM L1：DOM级别1于1998年10月1日成为W3C推荐标准<br />	DOM L2：使用addEventListener注册事件<br />	DOM L3： DOM3级事件模块在DOM2级事件的基础上重新定义了这些事件，也添加了一些新事件类型<br />		- 焦点事件，当元素获得或者失去焦点时触发；<br />		- 鼠标事件，当用户通过鼠标在页面上执行操作时触发；<br />		- 滚轮事件，当使用鼠标滚轮（或类似设备）时触发；<br />		- 文本事件，当在文档中，输入文本时触发；input  <br />		- 键盘事件，当用户通过键盘在页面上执行操作时触发；
## 4.2 常见的事件类型
### 1）鼠标事件 
click 鼠标点击 <br />mouseenter 鼠标经过 <br />mouseleave 鼠标离开 

### 2）焦点事件 
focus 获得焦点 （光标）<br />blur 失去焦点 （光标）

### 3）键盘事件 
keydown键盘按下触发 <br />keyup 键盘抬起触发 

### 4）文本事件 
input 用户输入触发

### 5）表单提交事件
```javascript

let form=document.querySelector('form')
form.addEventListener('submit',function(e){
  // 阻止默认提交行为
    e.preventDefault()
})
```

### 6）change事件
鼠标离开表单，且当表单里的值发生变化时触发，和blur不一样<br />input事件只要输入就会触发
### 7）注意点
事件处理函数不会主动执行,必须触发才会执行, 触发一次就会重新执行一次<br />	事件处理函数里面的内容最后执行

# 5. 高阶函数
高阶函数：函数的高级应用，js中函数可以被当成值来对待（数字、字符串、布尔、对象） <br />1.函数表达式 let fn = function (){} <br />把函数当值赋值给变量

2.回调函数 如果将函数A作为参数传递给B时，函数A为回调函数 function fn （）{} setInterval（fn,1000） <br />此时fn就是回调函数，把fn当做setinterva的参数，不会立马执行，1秒后回去调用就是回调函数 box.addEventListener('click',function(){})
```html
  <script>
        let num = 10
        //函数表达式
        let fn = function () { }
        btn.onclick = function () { }
        // 高阶函数 函数的高级用法，把函数当值来看看

        //  回调函数

        // setInterval(function(){}, 1000)
        function fn() { }
        setInterval(fn, 1000)
        // 此时 fn 就是回调函数   回头去调用的函数

        box.addEventListener('click', fun)
        function fun() {

        }
    </script>
```
# 6. 环境对象
【函数内部】特殊的变量this，表示当前函数运行时所处的环境 <br />谁调用，this就是谁 <br />在函数内部，涉及到对象本身的操作 ，可以用this

# 7. 时间对象
时间对象：用来表示时间的对象
## 7.1 获取日期对象
new：实例化 <br />获得当前时间 let date = new Date( ) <br />获得指定时间 let date1 = new Date('1949-10-01 18:30:00') <br />要加引号，字符串<br />把要获得时间对象的时间当成参数传入
```html
  <script>

        // new 实例化 时间对象
        // 小括号为空可以得到当前的时间
        let date = new Date()
        console.log(date)
        // 小括号里面写上时间，可以返回指定的时间 
        let last = new Date('2021-8-29 18:30:00')
        console.log(last)
    </script>
```

## 7.2 时间对象方法
ate.getFullYear（） 获得年份 <br />date.getMonth()+1   月份0——11，要加1 <br />date.getDate() 获得日期 <br />时分秒 date.getHours() <br />date.getMinutes() <br />date.getSeconds()<br /> // 星期几，星期天返回0 date.getDay()<br />newDate().toLocaleString() 获得当前 时间，固定格式 2022/5/28 15:03:45
```html
  <script>
// 先把时间实例化为对象，再进行操作
        let date = new Date()

        // 获得当前年份
        console.log(date.getFullYear())
            // 获得当前月份 （值为0-11），最终要加1
        console.log(date.getMonth() + 1)
            // 获得当前日期
        console.log(date.getDate())
            // 时分秒
        console.log(date.getHours())
        console.log(date.getMinutes())
        console.log(date.getSeconds())
            // 星期几，星期天返回0
        console.log(date.getDay())
    </script>
```
## 7.3 补0
三元表达式<br />时间变量<10? ’0‘+时间变量 ：时间变量

## 7.4 时间戳
时间戳：毫秒数，是一种特殊的计量时间的方式，是独一无二的 <br />场景：计算倒计时 <br />将来时间9.1 12：00  有一个时间戳 20000 <br />现在时间8.29 15：00 有一个时间戳 10000 <br />可以用将来是时间戳减去现在 的时间戳，就是剩余的时间戳 
### 1）3种方式获取时间戳 
1.实例化时间对象 date .getTime（）<br /> 2.+ new Date（） <br />前两种可以返回指定时间的时间戳 ，在括号里写‘年份-月-日 时：分 ：秒’ ，<br />括号里不写就是返回现在的时间戳<br />3.Date.now() 只能返回当前的时间戳 

### 2）时间戳转换为时分秒
预计下班时间戳 - 当前时间戳         <br />let end = +new Date('2022-4-22 22:00:00')        <br /> let start = +new Date()         <br />let total = (end - start) / 1000 //得到总秒数             <br />// let d = parseInt(total / 60 / 60 / 24) //计算天        <br /> let h = parseInt(total / 60 / 60 % 24) //计算小时        <br /> let m = parseInt(total / 60 % 60) //计算分钟        <br /> let s = parseInt(total % 60) //计算秒<br />	
```html
  <script>

        // 3种方式获取时间戳
        // 方法一：date .getTime（）  getTime是一种方法，必须要加小括号

        // let date = new Date ()
        // console.log(date.getTime())


        // 方法二 + new Date（） 加 号转换成数字型
        console.log(+new Date())
            // 可以返回 指定时间的时间戳
        console.log(+new Date('2022-4-20 12:00:00'));

        // 方法三：Date.now() 只能得到当前的时间戳
        // console.log(Date.now())
    </script>
```

# 8. 事件对象
## 8.1 获取事件对象
在事件里面接受一个形参即可<br />元素.addEventListener（‘click’，function（e){ } <br />e也是个对象，有事件触发时的相关信息<br /> 在事件绑定的回调函数的第一个参数就是事件对象

## 8.2 事件对象常用属性
1.type 获取当前的事件类型 <br />2.clientX/clientY 获取光标相对于浏览器可见窗口的位置 <br />3.PageX/PageY 获取整个文档的位置 <br />4.offsetX/offsetY 获取光标相对于当前Dom元素的位置 <br />（以上位置得到的值是数字）<br />5、key 用户按下键盘的值<br />事件对象 键盘e.key  只要e.key === “'' <br />e.keyup,获取的是当前这一次的value<br /> e.keydown 获取的是上一次的value<br />keydown经常用于拖拽 <br />keyup用于发布、搜索<br />注意： 不建议再使用 keyCode
## 8.3 自动触发事件	
事件源.事件名（）

## 8.4 事件流
事件完整执行过程中的流动路径
### 1）事件捕获阶段：父到子 
addEventlistener第三个参数传入true代表捕获阶段触发（很少使用），true，而且父到子都要添加true 
```html
<body>
    <div class="father">
        <div class="son"></div>
    </div>
    <script>
        let fa = document.querySelector('.father')
        let son = document.querySelector('.son')
        fa.addEventListener('click', function () {
            alert('我是爸爸')
        }, true)
        son.addEventListener('click', function () {
            alert('我是儿子')
        }, true)
        document.addEventListener('click', function () {
            alert('我是爷爷')
        }, true)

    </script>
</body>

```



### 2）事件冒泡阶段：子到父 
addEventlistener第三个参数默认false，冒泡阶段触发（常用） <br />当一个元素被触发事件后，会依次向上调用【所有父级元素】的【同名】事件
```html
<body>
    <div class="father">
        <div class="son"></div>
    </div>
    <script>
        let fa = document.querySelector('.father')
        let son = document.querySelector('.son')
        fa.addEventListener('click', function () {
            alert('我是爸爸')
        })
        son.addEventListener('click', function () {
            alert('我是儿子')
        })
        document.addEventListener('click', function () {
            alert('我是爷爷')
        })

    </script>
</body>

```

### ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1653727262135-97a1c50d-e755-4772-b4ae-236c6d9b78c5.png)
事件 捕获：点击儿子，先弹出爷爷，然后是爸爸，最后是儿子<br />点击爸爸，先弹出爷爷，然后是爸爸

事件委托：点击儿子，先弹出儿子，然后是爸爸，然后是爷爷<br />点击爸爸，先弹出爸爸，然后是爷爷<br />	<br />事件冒泡的必要性<br />			如果没有冒泡.给大盒子注册点击事件, 点击的是里面的小盒子,会导致大盒子的点击无法执行 

### 3）阻止事件冒泡
#### ① 阻止事件流动 
把事件限制在当前元素 <br />需要拿到事件对象 <br />事件对象.stopPropagation() 
```html
<body>
    <div class="father">
        <div class="son"></div>
    </div>
    <script>
        let fa = document.querySelector('.father')
        let son = document.querySelector('.son')
        fa.addEventListener('click', function () {
            alert('我是爸爸')
            e.stopPropagation()
        })
        son.addEventListener('click', function () {
            alert('我是儿子')
           // 阻止流动 Propagation 传播
            e.stopPropagation()
        })
        document.addEventListener('click', function () {
            alert('我是爷爷')
        })
      
      点击儿子后，只显示‘我是儿子’，没有再往上显示了

    </script>
</body>

```

mouseover，mouseout会有冒泡效果 <br />mouseenter，mouseleave没有冒泡效果（推荐）

#### ② 阻止默认行为 
比如链接点击不跳转,表单域的不提交 <br />e.preventDefault()
```html
<body>
    <a href="http://www.baidu.com">跳转到百度</a>
    <script>
        let a = document.querySelector('a')
        a.addEventListener('click', function (e) {
            // 阻止默认行为 方法
            e.preventDefault()
        })
    </script>
</body>
```

### 3）事件委托
优点：给父级元素加事件 原理:利用事件冒泡，给父元素添加事件，子元素可以触发 实现：事件对象.target可以获得真正触发事件的元素	<br />自己不注册事件,将对应的事件注册给祖先元素<br />				减少事件的注册,提高效率<br />				e.target => 当前点击的那个元素<br />		阻止事件冒泡<br />			1. 先要明确那一块区域不能冒泡<br />			2. 需要阻止什么事件传递就给这块区域的最大盒子注册该事件<br />			3. 在事件处理函数里面接受事件对象, 并添加上e.stopPropagation()<br />	
### 4）事件注册和解绑
#### 		① 传统on注册
			同一个对象,后面注册的事件会覆盖前面注册(同一个事件)<br />			直接使用null覆盖偶就可以实现事件的解绑<br />			都是冒泡阶段执行的
#### 		② 事件监听注册
			语法: addEventListener(事件类型, 事件处理函数, 是否使用捕获)<br />			后面注册的事件不会覆盖前面注册的事件(同一个事件)<br />			可以通过第三个参数去确定是在冒泡或者捕获阶段执行<br />			必须使用removeEventListener(事件类型, 事件处理函数, 获取捕获或者冒泡阶段)<br />				匿名函数无法被解绑<br />	
```html
<body>
    <button>点击</button>
    <script>
        let btn = document.querySelector('button')
            // 1.l0 on
            // 多次相同的事件，只执行最后一次
            // btn.onclick = function () {
            //     alert('第一次')
            // }
            // btn.onclick = function () {
            //     alert('第二次') 
            // }
        只弹出第二次
            // 解绑事件
            // btn.onclick = null
        
        
            // 2. addEventListener
        btn.addEventListener('click', add)

        function add() {
            alert('第一次')
        }
        btn.addEventListener('click', function() {
                alert('第二次')
            })
      
      先弹出第一次，然后弹出第二次
            // btn.removeEventListener('click', add)
      只能解绑具名函数
    </script>
```

## 

# 9. bom浏览器对象
## 9.1 bom和dom对比
DOM：<br />文档对象模型<br />把文档当作一个对象来看待<br />顶级对象是 document<br />主要学习的是操作页面元素<br />是 W3C 标准规范

BOM：<br />浏览器对象模型<br />把浏览器当作一个对象来看待<br />顶级对象是 window<br />学习的是浏览器窗口交互的一些对象<br />是浏览器厂商在各自浏览器上定义的，兼容性较差

## 9.2 bom构成
BOM 比 DOM 更大，它包含 DOM<br />window是bom的顶层对象 <br />包含 document、location、navigation、screen、history等子对象<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1654073561292-df3e6d76-60f1-41be-84f2-5f877c791ef0.png)

## 9.3 window 
1. window对象是一个全局对象，也可以说是JavaScript中的顶级对象<br />2. 像document、alert()、console.log()这些都是window的属性和方法，基本BOM的属性和方法都是window的。<br />3. 所有通过var定义在全局作用域中的变量、函数都会变成window对象的属性和方法<br />4. window对象下的属性和方法调用的时候可以省略window<br />当调用 window 下的属性和方法时，可以省略 window。 alert(1); 完整写法 window.alert(2);
### 1） 定时器-间歇函数
#### ① 开启定时器
setInterval（函数，间隔时间） <br />作用：每隔一段时间调用这个函数 根据时间自动重复执行某些代码 <br />间隔时间单位是毫秒 <br />1000毫秒=1秒 <br />注意：函数不用加大括号，返回值是数字（定时器的序号） 

#### ② 关闭定时器 
let 变量名 = setInterval（函数，间隔时间）<br />cleanInterval（变量）
#### ③ 注意点
定时器也是需要等待, 所以后面的代码先执行<br />每一次调用定时器,都会产生一个新的定时器

### 2）定时器-延时函数
#### ①开启延时器
window.setTimeout（回调函数，等待的毫秒数） <br />只执行一次，把一段代码延迟执行，平时省略window 
#### ②清除延时器
let timer = setTimeout（回调函数，等待的毫秒数） clearTimeout（timer）

```html
<body>
    <button id="btn1">解除延时器</button>
    <button id="btn2"> 开启延时器</button>
    <script>
        let btn1 = document.querySelector('#btn1')
        let btn2 = document.querySelector('#btn2')


        btn2.addEventListener('click', function() {

            let timer = setTimeout(function() {
                    console.log(111)
                }, 5000) // 仅仅执行一次
            console.log(timer) //还没调用的时候就有序号数字了，调用完后，数字+1

            // 开启后，解除定时器
            btn1.addEventListener('click', function() {
                clearTimeout(timer)
            })
        })
    </script>
</body>

```
#### ③ 注意点
延时器需要等待,所以后面的代码先执行<br />       设置延时器的时候就会有一个序号 <br />setTimeout  （回调函数，等待的毫秒数） =1，还没开始调用就有了，调用后，产生一个新的延时器，setTimeout  （回调函数，等待的毫秒数） =2<br />	每一次调用延时器都会产生一个新的延时器

#### ④ 定时器和延时器的区别
setInterval的特征是重复执行，首次执行会延时<br />setTimeout的特征是延时执行，只执行1 次<br />setTimeout结合递归函数，能模拟setInterval重复执行<br />clearTimeout清除由setTimeout创建的定时任务

### 3）页面滚动事件
scroll 监听整个页面滚动 <br />滚动条在滚动的时候持续触发的事件<br />window.addEventListener('scroll',function(）{})

### 4）页面加载事件 
加载外部资源（如图片、外联css和JavaScript）加载完毕时触发的事件 load <br />监听页面所有资源加载完毕 <br />window.addEventListener('load'',function(）{}) <br />也可以针对某个资源添加load

只等dom加载，无需等待样式表，图片加载 DOMContentLoaded<br />document.addEventListener（‘ DOMContentLoaded’，function（）{})

### 5）resize事件
在窗口尺寸改变时触发事件<br />window.resize()
```html
 <script>
        // 当窗口变化时触发的事件
        window.addEventListener('resize', function() {
            console.log(document.documentElement.clientWidth);

            let w = document.documentElement.clientWidth
            if (w >= 1920) {
                document.body.style.backgroundColor = 'pink'

            } else if (w > 540) {
                document.body.style.backgroundColor = 'hotpink'
            } else {
                document.body.style.backgroundColor = 'deeppink'
            }


        })
    </script>
```
### 6）递归函数
自己调用自己就是递归函数 <br />在函数里面自己调用自己，要加退出调节，否则会死循环 
```html
 <script>
        // 递归函数 ： 自己调用自己就是递归函数
        // 递归函数容易造成死递归，一定要加退出条件
        let num = 0
        function fn() {
            num++
            console.log(111)
            // 在函数里面，调用自己  
            if (num >= 100) {
                return
            }
            fn()
        }
        fn()
    </script>
```
#### 递归函数结合延时器
```html
<body>
    <div></div>
    <script>
        // 利用递归函数 模拟了 setinterval
        let div = document.querySelector('div')
        function fn() {
            div.innerHTML = new Date().toLocaleString()
            setTimeout(fn, 1000)
        }
        fn()
    </script>
</body>
```

## 9.4 window子对象
### 1）location对象

#### ① location.href
console.log(location.href) = '本网页地址 '<br />直接改写，可以立即自动跳转页面

#### ② location.search 
获取地址中的问号？后面的内容console.log(location.search) 

#### ③ location.hash 
获取地址中的哈希值，符号#后面的部分 console.log(location.hash) 


#### ④ location.reload()   
// 刷新方法:有本地缓存，也有强制刷新ctrl+f5 =reload（true ）<br />reload()方法用于刷新当前文档。会从缓存获取当前文档。<br />reload() 方法类似于你浏览器上的刷新页面按钮。<br />如果把该方法的参数设置为 true，那么无论文档的最后修改日期是什么，它都会绕过缓存，从服务器上重新下载该文档。

### 2）navigator对象
navigator对象<br />	主要用来获取浏览器的信息<br />	navigator.userAgent<br />	案例: 判断设备<br />		navigator.userAgent 在这个字段里面判断是否有Mobile字段.  如果有表示是手机,反之则表示PC<br />		
```html
 <script>
        // 检测 userAgent（浏览器信息）
        !(function () {
            const userAgent = navigator.userAgent
            // 验证是否为Android或iPhone
            const android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)
            const iphone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)
            // 如果是Android或iPhone，则跳转至移动站点
            if (android || iphone) {
                location.href = 'http://m.itcast.cn'
            }
        })()

    </script>
```
### 3）history对象
管理历史记录<br />	history.forward()<br />	history.back()<br />	history.go()

```html
<body>
    <button class="forward">前进</button>
    <button class="back">后退</button>
    <script>
        let qianjin = document.querySelector('.forward')
        let houtui = document.querySelector('.back')
        qianjin.addEventListener('click', function () {
            // history.forward()
            history.go(1)
        })
        houtui.addEventListener('click', function () {
            // history.back()
            history.go(-1)
        })
    </script>
</body>
```

### 4) localStorage 本地存储对象
1.生命周期永久生效，除非手动删除，否则关闭页面也会 存在 <br />2.可以多 窗口（页面）共享（同一浏览器） <br />3.以键值对方式存储使用 
#### ① 语法：存、取、删
1.存储数据 localStorage.setItem('键'，‘值’)<br /> f12 application localstorage  查看<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1654739310625-241608dc-ac19-49a5-9e30-f3773fd5146f.png)


2.获取数据 localStorage.getItem(键'') <br />3.删除数据   localStorage.removeItem(键'') 

```html
 <script>
        // 本地存储只能存储字符串 
        // 1.存储数据 localStorage.setItem('键','值')
        localStorage.setItem('uname', 'pink老师')
            // 2.获取数据
        console.log(localStorage.getItem('uname'));
        // 3.删除数据 
        localStorage.removeItem('uname')

        // 存储复杂数据类型
        // 看不懂  要转换格式
        let obj = {
            uname: '刘德华',
            age: 18,
            address: '黑马'
        }


        // console.log(JSON.stringify(obj));
        // 1.复杂数据类型一定要转换成JSON字符串再进行存储

        localStorage.setItem('obj', JSON.stringify(obj))
            //JSON 属性和值都是双引号
            // let obj = {
            //     " uname": "刘德华",
            //     "age": " 18",
            //     "address": "黑马"
            // }
            // 2.取复杂数据
            // 获取的值是字符串，不是对象，不能直接使用，所以要转换
            // console.log(localStorage.getItem('obj'));字符串
            // 使用JSON.parse()将json字符串转换为对象
        console.log(JSON.parse(localStorage.getItem('obj')));
```
#### ② 存储复杂数据类型
本地只能存储字符串,无法存储复杂数据类型.需要将复杂数据类型转换成JSON字符串,再存储到本地<br />	转换成JSON字符串的语法<br />		JSON.stringify(复杂数据类型)<br />			将复杂数据转换成JSON字符串<br />		JSON.parse(JSON字符串)<br />			将JSON字符串转换成对象

## 9.5 js执行机制
### 1） js单线程
同一时间只能做一件事 <br />所有任务需要排队，前一个结束才会执行后一个。 

### 2）同步任务和异步任务
#### ①同步任务
同步任务都在主线程上执行，执行栈 

#### ② 异步任务 
异步任务放到任务队列里面

回调函数 <br />1.普通事件：click <br />2.资源加载：load <br />3.定时器：setInerval 、setTimeout，即使定时器定时为0

#### ③区别
执行的顺序不相同 <br />1.先执行执行栈里的同步任务 <br />2.异步任务放入任务队列中 <br />3.一旦执行栈中所有同步任务执行完毕，系统就会按次序读取任务队列中的异步任务，结束等待状态，进入执行栈，开始执行

#### ④事件循环
1.主线程执行完毕，查询任务队列，取出一个任务，推入主线程处理，<br />2.重复该动作 由于主线程不断重复获得任务、执行任务，再获取任务、再执行，所以这种机制被称为事件循环 eventloop<br />![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1654077372462-301fd6c8-35ae-4560-9f05-acdde1e23a4f.png)

# 10.自定义属性
## 10.1 固有属性
标签天生自带的属性 比如class id title等, 可以直接使用点语法操作
## 10.2 自定义属性
由程序员自己添加的属性,在DOM对象中找不到, 无法使用点语法操作,必须使用专门的API
### 1）设置自定义属性	
元素.setAttribute('属性名'，‘值’)
### 2）得到自定义属性
元素.getAttribute('属性名'）
### 3）删除自定义数学
元素.removeAttribute('属性名') 
## 10.3 data-自定义属性
传统的自定义属性没有专门的定义规则,开发者随意定值,不够规范,所以在html5中推出来了专门的data-自定义属性	<br />直接在在标签上设置，一律以data-开头<br />以dataset对象方式获取，元素.dataset ——是一个Dom对象，<br /> 可以访问对象属性获取自定义的属性值

```html
<body>
    <div class="box" data-index="0" data-name="andy"></div>
    <script>
        // 设置自定义属性
        let box = document.querySelector('.box')
        // box.setAttribute('myid', 10)
        // console.log(box.getAttribute('myid'))
        console.log(box.dataset) //属于对象，可以访问对象属性获取自定义的属性值
        console.log(box.dataset.index)//0
    </script>
</body>
```
# 11.正则表达式
regular expression <br />一种模式 ，js中也是对象 <br />匹配字符串中字符组合 <br />用途：表单验证（匹配） <br />过滤掉页面中一些敏感词（替换），<br />或从字符串中获取我们想要的 特定部分（提取）

## 11.1 语法
1.定义规则 <br />2.查找，找到则返回 <br />定义： let 变量名 = /表达式/ <br />//是正则表达式字面量<br /> let reg  =// 

reg.test（）方法 检测是否匹配 <br />检测变量是否包含在后面 的字符串里，<br />返回布尔值 

reg.exec（） 用于检索（查找）符合规则的字符串<br />返回数组，找不到返回null  
```javascript
 <script>
        // 定义正则表达式   reg 里面存的是对象
        let reg = /前端/
        // 2. 检测是否匹配 test （重点）
        let str = '我们大家都在学前端'
        // console.log(reg.test(str))
        // 3. 检索 exec()
        console.log(reg.exec(str))  // 返回的是数组
    </script>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1656855388222-bafb9a4c-fc47-45af-892d-4a683ea5e7b3.png)
## 11.2 元字符
### 1）边界符
（表示位置，开头和结尾 ，必须 用什么开头，用什么结尾） <br />^& 精确匹配，开头和结尾是同一个人，只能有 一个字符 
```javascript
 <script>

        // ^ 开头
        console.log(/^哈/.test('二哈'))  // false 
        console.log(/^哈/.test('我开心的哈哈大笑'))  // false 
        console.log(/^哈$/.test('我开心的哈哈大笑'))  // false 
        console.log(/^哈$/.test('哈哈'))  // false 
        console.log(/^哈$/.test('哈'))  // true  精确匹配

    </script>
```

### 2）量词
（表示重复次数）<br />设定某个模式出现的次数 <br />注意：正则里不要出现空格

```javascript
<script>
     //*量词    n>=0
        console.log(/a*/.test('')) //真，*0次
        console.log(/a*/.test('aa')) //真，*2次
        console.log(/a*/.test('aaaaaaaaaaaa')) //真，*12次
        console.log(/a*/.test('b')) //真，*0次

        //+量词    n>=1
        console.log(/a+/.test('')) //假
        console.log(/a+/.test('aa')) //真，+2次
        console.log(/a+/.test('aaaaaaaaaaaa')) //真，+12次
        console.log(/a+/.test('b')) //假


        // ? 出现 0 || 1 
        console.log(/^a?$/.test(''))//true
        console.log(/^a?$/.test('a'))//true
        console.log(/^a?$/.test('aa'))//false


  </script>
```

+ 表示重复至少 1 次<br />	? 表示重复 0 次或1次<br />	* 表示重复 0 次或多次

```javascript
<script>
      //{n}    只能出现n次
        console.log(/^a{3}$/.test('a')) //假
        console.log(/^a{3}$/.test('aaa')) //真
        console.log(/^a{3}$/.test('aaaa')) //假
        console.log('------------');
        //{n,}    只能出现n次或更多
        console.log(/^a{3,}$/.test('a')) //假
        console.log(/^a{3,}$/.test('aaa')) //真
        console.log(/^a{3,}$/.test('aaaa')) //真
        console.log('------------');
        //{n,m}    只能出现n-m次  不能加空格
        console.log(/^a{3,6}$/.test('a')) //假
        console.log(/^a{3,6}$/.test('aaa')) //真
        console.log(/^a{3,6}$/.test('aaaa')) //真
        console.log(/^a{3,6}$/.test('aaaaaa')) //真
        console.log(/^a{3,6}$/.test('aaaaaaaa')) //假


  </script>
```

{m,n} 表示重复 m 到 n 次<br />{n}只能重复n次 <br />{n,}>=n次

### 3）字符类
#### ① []包含任意一个
后面的字符串只要包含[]中任意一个字符，就返回true
```javascript
<script>
      // []后面的字符串只要包含[]中任意一个字符，就返回true
        console.log(/[abc]/.test('')) //false
        console.log(/[abc]/.test('a')) //true
        console.log(/[abc]/.test('ab')) //true
        console.log(/[abc]/.test('abc')) //true
        console.log(/abc/.test('a')) //false
      // 如果[]精准匹配，只能有[]中其中一个值
        console.log(/^[abc]$/.test('a')) //true
        console.log(/^[abc]$/.test('ab')) //false
        console.log(/^[abc]$/.test('abc')) //false
        console.log('-- -- -- -- -- -- -- --')
  
  </script>
```
#### 
#### ② [-]连字符 表示范围 
```javascript
<script>
        //26个英文字母选其中 一个
        console.log(/^[a-z]$/.test('a')) //true
            //26个英文字母选其中 一个  不分大小写
        console.log(/^[a-zA-Z]$/.test('D')) //true
        console.log(/^[a-zA-Z]$/.test('DD')) //false
        console.log(/^[a-zA-Z0-9]$/.test('9')) //true
   //26个英文字母选其中 一个  不分大小写
        console.log(/^[a-zA-Z0-9-_]$/.test('9')) //true
  
  </script>
```
[a-z]  表示a 到z 26个英文字母都可以<br />[a-zA-Z]   表示大小写都可以<br />[0-9]  表示0~9 的数字都可以

注意：量词只限制离他最近的 <br />/[1-9] [0-9]{4,}/

#### ③ [^取反\]
 [^a-z\]除了a-z的都可以 

#### ④ .匹配换行符之外的任何单个字符 
#### ⑤ 预定义
\d 匹配0-9之间的任一数字 <br />\D 除了0-9之间的任一数字 <br />\w 匹配任意的字母 、数字、下划线 <br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1656857430209-21ec5046-d064-41a5-a6e4-f166ed437571.png)

## 11.3 修饰符
修饰符附加在正则表达式之后
### 1）修饰符i
/表达式/i.test('a')   true<br />/表达式/i.test('A')  true<br />	i 是单词 ignore 的缩写，正则匹配时字母不区分大小写

### 2）修饰符g
g 是单词 global 的缩写，匹配所有满足正则表达式的结果，用于替换<br />字符串.replace(/正则表达式/g，’替换的文本‘) ，<br />匹配所有满足表达式的内容，全局匹配 <br />多个过滤词 /词A | 词B/不能加空格，否则会失效


# 12. 重绘和回流
回流 当渲染树中元素的尺寸、结构、布局发生变化的话，就会进行回流 <br />重绘，样式的改变，（不影响它在文档流中的位置和文档布局） <br />(比如：color、background-color、outline等改变)


场景：页面首次刷新 <br />浏览器窗口大小发生变化 <br />元素大小或位置 <br />字体大小 <br />内容增减 <br />激活css伪类 hover <br />脚本操作dom <br />面试题：重绘不一定引起回流，而回流一定会引起重绘
# 
# 12. 编程思想
## 12.1 排他思想 
通过第一个for给所有人绑定事件 <br />1.干掉所有人 使用第二个for循环统一修改所有人的样式 <br />2.复活他自己 this，改变当前样式 
```html
  <script>
         let btns = document.querySelectorAll('button')
        for (let i = 0; i < btns.length; i++) {
            btns[i].addEventListener('click', function () {
                // 干掉所有人
                for (let j = 0; j < btns.length; j++) {
                    btns[j].classList.remove('pink')
                }
                // 复活我自己
                this.classList.add('pink')
            })
        }
    </script>
```
另一种方法： 点击前，把场上之前唯一的那个pink类移除pink <br /> let pink = document.querySelector('.pink')                     <br />pink.classList.remove('pink')                    <br /> this.classList.add('pink')
```html
  <script>
         let btns = document.querySelectorAll('button')
        for (let i = 0; i < btns.length; i++) {
            btns[i].addEventListener('click', function () {
                // 我只需要找出那个唯一的 pink类，删除
                document.querySelector('.pink').classList.remove('pink')
                // 我的
                this.classList.add('pink')
            })
        }
    </script>
```
