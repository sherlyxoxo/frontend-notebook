# 1. 引入方式
## 1.1 内嵌式
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        p{
            color: red;
            font-size: 30px;
            background-color: green;
            width: 400px;
            height: 400px;
        }
    
    </style>
</head>
```
css写在style里 ，写在head里，title标签 下面     

```html
<style>
选择器（标签）{
属性名：属性值；
}
</style>
```



## 1.2 外链式
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
   <link rel="stylesheet" href="./my.css">
</head>
```
写在一个单独的css文件中，需要通过link标签在网页中引入 (写在title后，head标签 里 ）（项目中常用）



## 1.3 行内式
<标签 style="属性:属性值；属性:属性值"></标签>          

写在标签的style属性中（配合js使用），只能控制当前标签  

```html
<div style="color: green; font-size: 30px;">这是一个p标签</div>
```


# 2. CSS选择器-单一



## 2.1标签选择器

标签{属性：属性值}   

特点：选择的是一类标签，而不是单独一个    



## 2.2 类选择器

.类名{css属性名：属性值；}  
通过所有类名，找到页面中所有带这个类名的标签，设置样式   
1.属性class=“类名1  类名2"（类名：数字、字母、下划线、中划线，**但不能以数字或中划线开头 ）**  
**2.一个标签可以有多个类名，需要空格隔开**



## 2.3 多类名选择器：  
	1.减少代码量
	2.方便代码的后期维护
	3.多类名 与css的先后顺序有关系    与html结构里面的class类名顺序没有关系
	4.多类名的添加  以空格的形式


## 2.4 id选择器

#id属性值{css属性名：属性值；}  
**1.id在一个页面中是唯一的，只能用一次**  
2.一个 id选择器只能选中一个标签  
3.id与class选择器的区别：  id的名字是唯一的（体现在js里面） class名字可以任意多个  



## 2.5 通配符选择器

*{css属性名：属性值；}  
**找到所有标签，设置样式,**  
**常用清除所有标签的默认margin和padding属性 ** 

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
          
      /* 1.标签选择器，选择所有这一标签*/
        p{
            color:green;
        }
      /* 2.类选择器，选择所有带这一类名的标签*/
        .red {
            color: hotpink;
        }
        .size  {
            font-size: 70px;
        }
     /* 3.id选择器，有且只有唯一一个该id的标签*/
        #blue  {
            color: khaki;
        }
     /* 4.通配符，选择html里所有的标签*/
       *{
           color: blue; 
        }
    </style>
</head>
<body>
    <p>标签选择器</p>
    <p class="red">类选择器</p>  
    <p>标签选择器</p>
    <p class="red size">类选择器</p>
    <div id="blue">id选择器</div>
</body>
</html>
```


# 3. CSS选择器-复合

![](https://cdn.nlark.com/yuque/0/2022/jpeg/27972378/1650609862917-9479693b-8f0d-45a5-a249-8df846df48d8.jpeg)
## 3.1 后代选择器
作用：根据html标签的嵌套关系，选择父元素后代中满足条件的元素  
**语法：（父级）元素1 （所有该子级）元素2{css}**  
元素2 可以是儿子，也可以是孙子等，只要是元素1 的后代即可  
元素1 和 元素2 可以是任意基础选择器（标签、类、id）  

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 后代 选择器，选择所有的后代 */
        div p{
            color: red
            ;
        }
    </style>
</head>
<body>
     <!-- 后代:儿子，孙子，重孙子…… -->
    <p>这是一个p标签</p>
    <div>
        <p>这是div的儿子p
            <p>这是div的孙子p</p>
        </p>
    </div>
</body>
</html>
```


## 3.2 子代选择器

只选择子代，不选择孙子，重孙子  
只能选择作为父元素的最近一级子元素。（简单理解就是选亲儿子元素）  
**选择器1＞选择器2{css}**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 后代选择器，全选中 */
        /* div a{
            color: red;
        } */

        div>a{
            color: red;
        }
        /* 子代选择器：只选中儿子 */


    </style>
</head>
<body>
    <!-- 空格隔开的是后代选择器，儿子孙子，重孙子都会选中 -->
   
    <div>
        父级
        <a href="#">这是div里的儿子a</a>
        <p>
            <a href="#">这是div里儿子p里的a</a>
        </p>
    </div>
</body>
</html>
```


## 3.3 并集选择器

并集选择器可以选择多组标签, 同时为他们定义相同的样式，通常用于集体声明  
逗号可以理解为和的意思  
**选择器1，选择器2{css}**  
**逗号后记得换行 **

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
          /* 逗号后记得换行 */
        h1,
        p,
        span
        {
            color: red;
        }

    </style>
</head>
<body>
    <h1>
        hahhahahah
    </h1>
    <p>aaaaaaaaa</p>
    <span>ooooooo</span>
    <div>
        sjsjsjs
    </div>
</body>
</html>
```


## 3.4 交集选择器

必须同时满足多个条件的才能被选中  
**选择器1选择器2{css}**  
**中间什么都不加**  
**标签.类**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
       /* 交集选择器，中间没有空格 */
          p.box{
            color: red;
        }

    </style>
</head>
<body>
    <!-- 找到第一个p，带box类，设置文字颜色是红色 -->
    <p class="box">这是p标签：box</p>
    <p>pppppp</p>
    <div class="box">这是div标签：box</div>
</body>
</html>
```


## 3.5 伪类选择器：hover  

悬停状态  
**选择器:hover{css}**  
任何一个标签都可以添加伪类，任何一个标签都可以悬停  

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
       /* 交集选择器，中间没有空格 */
          p.box{
            color: red;
        }

    </style>
</head>
<body>
    <!-- 找到第一个p，带box类，设置文字颜色是红色 -->
    <p class="box">这是p标签：box</p>
    <p>pppppp</p>
    <div class="box">这是div标签：box</div>
</body>
</html>
```


## 3.6  伪类选择器：focus

:focus 伪类选择器用于选取获得焦点的表单元素  
焦点就是光标，一般情况 <input> 类表单元素才能获取  
/* 获得焦点，把光标点到input里  
 失去焦点，光标离开input */  
/* 通过input：focus改变获得焦点的状态 */  

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
      input {
            width: 100px;
            height: 20px;
        /*(表单控件获取焦点时会默认显示 外部轮廓线，可通过outline设置）*/
            outline: none;
        }
        
        input:focus {
            border: 1px solid red;
        }
    </style>
</head>
<body>
     <input type="text">
</body>
</html>
```


## 3.7 属性选择器

通过元素上的html属性来选择 元素，常用于选择input  
①标签名[属性名]  
②标签名[属性=""]  
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
       input[type="text"]{
            background-color: pink;
        }
        input[type="password"]{
            background-color: skyblue;
        }
    </style>
</head>
<body>
 <input type="text" name="" id="">
    <input type="password" name="" id="">
</body>
</html>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651030095799-d55d9600-35ab-4635-afe9-b688f1eb45b7.png)



# 4. 字体与文本样式



## 4.1 字体



### 1）字体大小

font-size: 数字px;  
**默认16px**



### 2） 字体粗细
①font-weight：normal；（正常）   
font-weight：bold；（加粗）  
**②数字（不加单位）**  
**正常400，加粗700**



### 3） 字体样式（是否倾斜）

font-style：normal；（正常）-可去除\<i>标签倾斜作用  
font-style：italic；（倾斜）  



### 4） 字体类型

font-family  
无衬线字体sans-serif  
（黑体、arial）  
衬线字体serif  
宋体，times new roman  
等宽字体monospace、consolas、firacode  



### 5）字体颜色

字体颜色 color  

预定义的颜色值：red, green, blue    

十六进制：#FF0000,#FF6600  
#000000（#000），#ff0000（#f00）  
六个0，两两一组  
r：00  g：00 b：00  
两个 一组一样的，就可以省略  

RGB代码：rgb(255,0,0)或rgb(100%,60%,10%)  
rgba，a表示 透明度，取值 范围0-1  
透明的另一种写法 color：transparent； 



### 6）字体复合写法

font：style（值） weight（值） size（值） family（值）；  
可以省略，只能省略前2个



## 4.2 文本

### 1）text-ident 首行缩进
em（一个字所代表 的大小） 
px（1像素）  
单位 em   1em=16px  



### 2）text-align 水平对齐

内容(图片、文字、span、a、input、img标签）水平对齐  
text-align: left，左对齐  
text-align: center 居中对齐  
text-align: right右对齐  
图片在body里，要让它对齐标签选择器要选body（父元素）  

标签水平居中  
div、p、h（大盒子）水平居中  
margin：0 auto；  
***宽度和高度不要忘记加单位px**



### 3）text-decoration 文本装饰
underline，下划线  
line-through，删除线  
overline，上划线  
none，无装饰性，常用  



### 4）line-height 行高
注意： 当采用字体连写   不写行高默认是0  
会把上面的行高覆盖font:font-style font-weight font-size/line-height font-family  
**垂直居中：设置行高属性值=自身高度值**   
**只适用单行文字 **  
通常给body行高设置为1.5（不带单位），会直接继承给子元素，子元素根据自己的font-size再去计[算子](https://so.csdn.net/so/search?q=%E7%AE%97%E5%AD%90&spm=1001.2101.3001.7020)元素自己的line-height。



## 3. 基线

浏览器文字类型元素排版中存在 用于对齐的基线  
垂直对齐 方式   

浏览器遇到行内和行内块标签当做文字处理，默认文字按基线对齐（还可以转换显示模式：display：block）  
vertical-align:top  
middle  
bottom  

图片在垂直方向居中：  
1.在父级加行高，和高度一样  
2.图片设置vertical-align：middle  



# 5. 背景相关属性


## 5.1 背景颜色

background-color：颜色值；  
透明色：background-color: transparent  

rgba（0，0，0，0）默认透明  
红绿蓝三原色，a是透明度0-1  
0.5=.5，0可以省略  
背景半透明是指盒子背景半透明，盒子里面的内容不受影响  



## 5.2 背景图片

background-image :  none（默认无图）   
background-image :  url(图片路径地址)   



## 5.3 背景平铺

background-repeat：  
repeat （默认）水平和垂直方向都平铺  
no-repeat ，不平铺  
repeat -x沿水平方向x轴平铺  
repeat-y沿水平方向y轴平铺  

背景色和背景图可以同时显示  



## 5.4 背景图位置
background-position: x横向值  y纵向值 （中间空格不加逗号）  
默认位置-左上角，平铺：background-position: 0  0；  
x和y值  
①方位名词：水平（left，center，right）  
垂直（top，center，bottom）  
全居中：background  position：center；  
可以只写一个center  

②x，y轴像素  
（50px 50px）**要写单位**  
基于0 0 左上起始位置移动，正数往右，下移动  
负数，往左（上）走，超过盒子的位置就不显示  

③百分数，不加单位  
（50% 50%）居中  
基于0 0 左上起始位置移动，正数往右，下移动  
负数，往左（上）走，超过盒子的位置就不显示  

注意：背景图位置如果是英文可以颠倒位置，如果是数值不能颠倒顺序  


## 5.5 背景图缩放
background-size：宽度 高度 （数字+px）    

常用：  
1.百分比： 相对于当前盒子自身的宽高百分比   
100%随着盒子的宽度大小而缩放，适合移动响应式   

2.contain： 等比例缩放，直到不会超出盒子的最大   
/* 如果图的宽或者高与盒子的尺寸相同了，另一个方向停止缩放，导致盒子可能有留白 */  

3.cover：将背景图片等比例缩放，直到刚好填满整个盒子   



## 5.6 背景复合属性

**background：color image repeat position/size**  
省略：按照需求省略  
只写缩放也要写位置0 0/cover  



## 5.7 背景颜色渐变 
多个颜色逐渐变化 bgi：linear-gradient（ 颜色1， 颜色2）  
 默认从上到下过渡（从颜色1-2）  
 transparent（透明色）    
background-image: linear-gradient(  
transparent,  
rgba(0,0,0,.5)  
 );  



# 6. 元素显示模式


## 6.1 块级元素

显示特点  
①独占一行  
②可以设置宽高  
③宽度默认和父级标签一样  
④是一个容器及盒子，里面可以放行内或者块级元素。  
⑤文字类的元素内不能放块级元素  
**代表标签：div、p、h、ul、li、ol、dl、dt、dd、form、header、nav、footer**



## 6.2 行内元素

显示特点  
①一行可以显示多个  
②不可以设置宽高  
③尺寸和内容的大小相同  
④行内元素只能容纳文本或其他行内元素，不能放块元素或行内块  
⑤特殊情况链接 \<a> 里面可以放块级元素，但是给 \<a> 转换一下块级模式最安全  
**代表标签:a、span、b、u、i、s、em、strong、del**  



## 6.3 行内块元素

显示特点：  
①一行可以显示多个  
和相邻行内元素（行内块）在一行上，但是他们之间会有空白缝隙。  
②宽高，行高、外边距以及内边距都可以控制（块级元素特点）  
③默认宽度就是它本身内容的宽度（行内元素特点） 

代表标签：  
**input、textarea、botton、select、td、（img）……** 
特殊情况：img标签有行内块元素特点，但是chrome调试工具显示结果是in-line  



## 6.4 显示模式转换

display：block 转换成块级元素  
display：inline-block 转换成行内块元素  
display：inline 转换成行内  



## 6.5 html嵌套规范注意点
1.块级元素一般作为大容器，可以嵌套：文本，块级元素，行内元素，行内块元素、、、  
**注意：p标签中不要嵌套div、p、h等块级元素**  

2.a标签内部可以嵌套任意元素  
**注意：a标签不能嵌套a标签**  



# 7.emmet语法


## 7.1 快速生成HTML结构语法

①生成标签 直接输入标签名 按tab键或enter即可   比如  div   然后tab 键， 就可以生成 \<div>\</div>  
②如果想要生成多个相同标签  加上 * 就可以了 比如   div*3  就可以快速生成3个div  
③如果有父子级关系的标签，可以用 >  比如   ul > li就可以了  
④如果有兄弟关系的标签，用  +  就可以了 比如 div+p  
⑤如果生成带有类名或者id名字的，  直接写  .demo  或者  #two   tab 键或enter就可以了  
⑥如果生成的div 类名是有顺序的， 可以用 自增符号  $   
⑦如果想要在生成的标签内部写内容可以用  { }  表示  



## 7.2 快速生成CSS样式语法
	CSS 基本采取简写形式即可  
	比如 w200   按tab  可以 生成  width: 200px;  
	比如 lh26px   按tab  可以生成  line-height: 26px;  


## 7.3 格式化代码

自动排版  
快捷键shift+option +f = 右键format document  
 保存页面的时候自动格式化代码  
	1）文件 ------.>【首选项】---------->【设置】；  
	2）搜索emmet.include;  
	3）在settings.json下的【工作区设置】中添加以下语句：  
	"editor.formatOnType": true,  
	"editor.formatOnSave": true  
