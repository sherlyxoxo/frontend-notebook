# 1.CSS三大特性
## 1.1 继承性
特性：子元素有默认继承父元素某些样式的特点（子承父业）<br />**文字控制属性的都可以继承**<br />1.color<br />2.font-style、font-weight、font-size、font-family<br />3.text-indent、text-align<br />4.line-height<br />行高可以跟单位也可以不跟单位<br />如果子元素没有设置行高，则会继承父元素的行高为 1.5 倍数<br />此时子元素的行高是：当前子元素的文字大小 * 1.5<br />body 行高 1.5  这样写法最大的优势就是里面子元素可以根据自己文字大小自动调整行高<br />……<br />注意点：可以通过调试工具判断样式是否可以继承inherited

**(拓展）继承失效的特殊情况**<br />**1.a标签的color会继承失效**<br />**2.h系列的font-size会继承失效（会变，不会完全变）**
## 1.2 层叠性
特性：1.相同的覆盖，2.不同的叠加<br />相同选择器给设置相同的样式，此时一个样式就会覆盖（层叠）另一个冲突的样式<br />样式冲突，遵循的原则是就近原则，哪个样式离结构近，就执行哪个样式<br />注意点：只有选择器优先级相同时，才能通过层叠性判断结果
## 1.3 优先级
当同一个元素指定多个选择器，就会有优先级的产生<br />	选择器相同，则执行层叠性<br />	选择器不同，则根据选择器权重执行<br />    优先级高的选择器样式会覆盖优先级低选择器<br />**公式：继承＜通配符＜标签＜类＜id＜行内样式＜！important**<br />（更精准地选到标签，优先等级更高）
## 1.4 优先级权重叠加计算
如果是复合选择器，需要通过权重叠加计算方式。<br />公式：（每一级之间不存在进位）<br />复合选择器中：（行内样式个数，id选择器的个数，类选择器的个数，标签选择器的个数）<br />（style，#，.,标签）<br />规则<br />1.先比较第一级数字，如果比较出来了，之后的统统不看，<br />……<br />4.如果最终所有数字都相同，看层叠。<br />注意点：！important如果不是继承，权重最高。（慎重使用）<br />**标签只选中父集就是继承，优先级最低，加important也没用。**<br />其次按公式数数<br />**都是继承，看最近的父级，第一继承，**<br />(不同的标签是继承，相同的标签是后代）

注意点：<br />1.！important写在属性值的后面，分号的前面<br />2.！important不能提升继承的优先级，只要是继承就是优先级最低的(! IMPORTANT不能给继承的加）
# 2. 盒子模型
作用：用来布局，摆内容，摆标签<br />盒子：标签，标记，元素
## 2.1 构成
盒子模型（Box Model）组成<br />	把 HTML 页面中的布局元素看作是一个矩形的盒子，也就是一个盛装内容的容器<br />	边框、外边距、内边距、实际内容<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650684797425-5eed9410-d7d5-4a0b-b352-64c64b3d1cb7.png)

## 2.2 内容
设置宽、高，影响的是content<br />width/height ：数字+px；
## 2.3 边框 border
### 1）复合属性
border：粗细 线条(solid实线，dashed虚线，点线dotted）颜色； 空格隔开<br />border：10px solid red；<br />快捷键：bd+tab
### 2) 边框方向
默认4个方向都加边框线<br />单方向设置<br />border-方位名词（top、bottom、left、right）
### 3）border-collapse
表格的细线边框<br />	border-collapse 属性控制浏览器绘制表格边框的方式，它控制相邻单元格的边框<br />	 border-collapse:collapse; 表示相邻边框合并在一起<br />常用于表格
### 4）边框对盒子实际大小的影响
边框会额外增加盒子的实际大小<br />测量盒子大小的时候,不量边框。<br />如果测量的时候包含了边框,则需要 width/height 减去边框宽度

### 5）用边框画三角形
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
         div {
            width: 0;
            height: 0;
            /* background-color: pink; */
            border-top: 10px solid transparent;
            border-left: 10px solid transparent;
            border-right: 10px solid blue;
            border-bottom: 10px solid transparent;
        }
    </style>
</head>
<body>
       <div></div>
</body>
```
①设置一个盒子<br />②设置四周不同颜色的边框，边框宽度大一些<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651031111501-1fefe533-581f-4028-bf63-6e93f06b5241.png)

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651031119672-f521f309-b458-47e2-83cb-4f3e795a7c42.png)<br />③将盒子宽高设为0，仅保留边框<br />![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651031131065-7a41beda-f9f5-435b-8dc5-f56529954fc1.png)<br />④保留其中一个方向，其他的颜色设置为透明<br />![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651031147042-29337aa5-158e-4f9b-8db3-a4ac28dc144b.png)

### 6）圆角边框
属性名：border-radius（半径）<br />数字+px、百分比<br /> <br /> <br />最多连接4个，从左上角开始赋值，顺时针，没有 赋值的看对角<br /> <br /> 一个值表示4个角是相同的 <br /> border-radius: 10px;<br /> <br />常见应用<br />1.正圆<br />①盒子必须是 正方形<br />②设置边框圆角为盒子的一半 border-radius：50%<br /> <br />2.胶囊按钮<br />①盒子是长方形<br />②border-radius：值是高度的一半px

## 2.4 内边距padding
padding 属性用于设置内边距，即边框与内容之间的距离。

### 1）方向和值
默认添加4个方向的内边距<br />单独添加padding-left、padding-right、padding-topadding-bottom


padding属性可以当做复合属性使用，<br />padding最多取4个值（要写单位）<br />上 右 下 左<br />取3个值 <br />上 （左右） 下 <br />两个值<br />（上下）  （左右）<br />*顺时针，从上到右，没有看对面

padding写0，可省略单位

### 2）内边距会影响盒子实际大小
如果盒子已经有了宽度和高度，此时再指定内边框，会撑大盒子<br />（工作中：padding会把盒子自动撑开，盒子不写高，用padding更灵活。padding-bottom一般省略<br />不给可以写0，用padding复合属性）<br />盒子本身没有指定width/height属性, 则此时padding不会撑开盒子大小。<br />如果保证盒子跟效果图大小保持一致，则让 width/height 减去多出来的内边距大小即可

## 2.5 外边距 margin
margin 属性用于设置外边距，即控制盒子和盒子之间的距离<br />设置方式和内边距一样
### 1）水平居中
盒子必须指定了宽度（width）。<br />盒子左右的外边距都设置为 auto 。<br />margin:0 auto

常用于版心居中<br />版心：网页的有效内容
### 2）外边距合并
#### 相邻块元素垂直外边距的合并
当上下相邻的两个块元素（兄弟关系）相遇时，<br />如果上面的元素有下外边距 margin-bottom，下面的元素有上外边距 margin-top ，<br />则他们之间的垂直间距不是 margin-bottom 与 margin-top 之和。

取两个值中的较大者这种现象被称为相邻块元素垂直外边距的合并。	<br />	解决方案：尽量只给一个盒子添加 margin 值<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650700698133-f569308e-b3d9-4e51-9b17-46ea2795ff7d.png)

#### 嵌套块元素垂直外边距的塌陷
对于两个嵌套关系（父子关系）的块元素，父元素有上外边距同时子元素也有上外边距，子元素在父元素内部的margin不生效，此时父元素会塌陷较大的外边距值,<br />	<br />解决方案：<br />①可以为父元素定义上边框。<br />②可以为父元素定义上内边距。<br />③ 可以为父元素添加 overflow:hidden。(推举)<br />④把块标签，变成行内块<br />⑤设置浮动

## 2.6 清除内外边距，盒子实际大小
*{margin:0 <br />padding:0<br />box-sizing: border-box}<br />不用每个都加内减模式了

## 2.7 行内元素的内外边距问题
margin padding 水平方向可以生效<br />如果想要改变行内标签的内外边距垂直方向靠line-height 
# 3. 圆角和阴影
## 3.1 圆角
border-radius 属性用于设置元素的外边框圆角<br />border-radius: 圆的半径值px;（或盒子的百分比）<br />复合写法，最多4个值，从左上角开始赋值，顺时针，没有赋值的看对角<br /> 只有一个值表示4个角是相同的 

四个角可以分别设置圆角：<br />- 左上角 border-top-left-radius<br />- 右上角 border-top-right-radius<br />- 右下角 border-bottom-right-radius <br />- 左下角 border-bottom-left-radius

常见应用<br />1.正圆<br />①盒子必须是 正方形<br />②设置边框圆角为盒子的一半 border-radius：50%<br /> <br />2.胶囊按钮<br />①盒子是长方形<br />②border-radius：值是高度的一半px

## 3.2 盒子阴影
语法：复合写法  box-shadow: h-shadow v-shadow blur spread color inset; <br />数值要加单位px，空格隔开<br />h-shadow：必需。水平阴影的位置。允许负值<br />v-shadow：必需。垂直阴影的位置。允许负值<br />blur：可选。模糊距离。<br />spread：可选。阴影的尺寸。<br />color：可选。阴影的颜色。请参阅CSS颜色值。<br />inset：可选。将外部阴影（ outset）改为内部阴影,不写就是默认外部阴影。
```html
 .box {
            width: 300px;
            height: 300px;
            background-color: pink;
            box-shadow: 10px 20px 30px 10px red;
        }

```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650707346978-a7579374-6657-4395-8cbb-fa3d7212c9b5.png)
## 3.3 文字阴影
复合属性：语法 text-shadow: h-shadow v-shadow blur color;<br />h-shadow：必需。水平阴影的位置。允许负值<br />v-shadow：必需。垂直阴影的位置。允许负值<br />blur：可选。模糊的距离<br />color：可选。阴影的颜色
```html
 span {
            text-shadow: 10px 20px 30px red;
        }

```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650708024716-e51f8bcf-9e6e-4093-879a-d6cc6ac7b394.png)
# 4. 结构伪类&伪元素
## 4.1 结构伪类选择器
1.作用：根据元素在HTML中的结构关系查找元素<br />2.常用于查找某父级选择器中的子元素<br /> <br />E：first-child{} 父元素中第一个子元素，并且是E元素<br />E：last-child{}<br />E：nth-child（数字）{} <br />表示第几个<br />E：nth-last- child(数字）{}<br />倒数第几个
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 选中第一个 */
        li:first-child{
            background-color: green;
        }
        li:last-child{
            background-color: pink;
        }

        /* 中间 的任意一个 */
        li:nth-child(3){
            background-color: red;
        }

        
    </style>
</head>
<body>
    <!-- ul>li{这是第$个li}*8 -->
    <ul>
        <li>这是第1个li</li>
        <li>这是第2个li</li>
        <li>这是第3个li</li>
        <li>这是第4个li</li>
        <li>这是第5个li</li>
        <li>这是第6个li</li>
        <li>这是第7个li</li>
        <li>这是第8个li</li>
    </ul>
</body>
```
## ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650942362429-f0b7f591-7973-4246-97cc-6b4cf1c5f8ba.png)
## 4.2 结构伪类公式
在小括号写公式（）<br />n的注意点<br />1.n为0、1、2、3、4、5<br />2.常见 公式<br />①偶数：2n<br />②奇数 2n+1<br />③找到前5个<br />④找到第5个往后n+5
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        /* 偶数 */
      /* li:nth-child(2n){ */
          /* background-color: green; */
      /* } */

      /* 奇数 */
      li:nth-child(2n+1){
          background-color: green;
      }


      /* 几n就是几的倍数 */
      li:nth-child(4n){
          background-color: black;
      }


        
    </style>
</head>
<body>
    <!-- ul>li{这是第$个li}*8 -->
    <ul>
        <li>这是第1个li</li>
        <li>这是第2个li</li>
        <li>这是第3个li</li>
        <li>这是第4个li</li>
        <li>这是第5个li</li>
        <li>这是第6个li</li>
        <li>这是第7个li</li>
        <li>这是第8个li</li>
    </ul>
</body>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650942362429-f0b7f591-7973-4246-97cc-6b4cf1c5f8ba.png)
## 4.3 结构伪类-易错
想改变li标签里的a元素，选择的是第几个li，而不是第几个a
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
        /* /* 第一个li里的a * 先找到第一个li，然后用后代选择器/ */
        /* li:first-child a{ */
            /* color: red; */
        /* } */

        
        /* 找第一个li里第3个a */
        li:first-child a:nth-child(3){
            color:red;
        }


    </style>
</head>
<body>
    <ul>
        <li><a href="">这是li里第1个a1</a>
            <a href="">这是li里第1个a2</a>
            <a href="">这是li里第1个a3</a>
            <a href="">这是li里第1个a4</a>
            <a href="">这是li里第1个a5</a>
        </li>

        <li> <a href="">这是li里第2个a</a></li>
        <li><a href="">这是li里第3个a</a></li>
        <li> <a href="">这是li里第4个a</a></li>
        <li><a href="">这是li里第5个a</a></li>
        <li> <a href="">这是li里第6个a</a></li>
        <li><a href="">这是li里第7个a</a></li>
        <li><a href="">这是li里第8个a</a></li>
    </ul>
</body>
```
## 4.4 伪元素
由css模拟出的标签效果<br />（装饰性，不重要的小图）

父元素::before 在父元素的内容最前添加一个伪元素<br />父元素::after，在父元素内容的最后添加一个伪元素

注意点：1，必须设置content属性才能生效<br />content：'   (文字内容） '；<br />2.，伪元素默认是行内元素（可以display转换模式）


```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
        .father{
            width: 300px;
            height: 300px;
            background-color: pink;
        }
        .father::before{
            /* 伪元素必须添加Content属性 */
            content:'老鼠';
            color: seagreen;
            width: 100px;
            height: 100px;
            background-color: blue;
            display: block;
        }
        .father::after{
            content:'大米';
        }
    </style>
</head>
<body>
    <!-- 找父集，在这个父集里面创建子级标签 -->
    <div class="father">
    爱
    </div>
</body>
```
# 5. 浮动
## 5.1 标准流
标准流（文档流），标签默认的排列方式<br />不能直接布局网页<br />1.块级（自动换行）<br />2.行内或行内块<br />（行内块：代码换行会产生空隙）
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
   /* 浏览器解析行内块或行内标签的时候，如果标签换行书写，会产生一个空格的空隙 */
        div{
            width: 100px;
            height: 100px;
            display: inline-block;
        }
        .one{
            background-color: pink;
        }
        .two{
            background-color: skyblue;
        }
    </style>
</head>
<body>
       <div class="one">
        111
    </div>
    <div class="two">
        222
    </div>
</body>
```
## ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650944017004-9e621cd9-fd0a-4360-b99c-933ff1a85858.png)
## 5.2 浮动的作用
为什么需要浮动？ 有很多的布局效果，标准流没有办法完成，此时就可以利用浮动完成布局。 因为浮动可以改变元素标签默认的排列方式.
## 5.3 浮动的语法
浮动语法<br />	选择器 { float: 属性值; }<br />	none 元素不浮动（默认值）;<br />left 元素向左浮动;<br />right  元素向右浮动
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
        div{
            width: 100px;
            height: 100px;}
           
        .one{
            background-color: pink;
            float: left;
        }
        .two{
            background-color: skyblue;
            /* float: right; */
            float: left;
        }
    </style>
</head>
<body>
       <div class="one">
        111
    </div>
    <div class="two">
        222
    </div>
</body>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651028187676-6c889550-1700-4a3f-b7af-5c4880755fd2.png)<br />一个设置left，一个设置right，会分别移动到盒子两端<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651028263428-6d20b37c-713b-4350-b634-18f72d606bb1.png)<br />两个都设置left，靠近盒子的左边，紧贴在一起<br />两个都设置right，靠近盒子的右边，紧贴在一起

## 5.4 浮动的特点
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
        .one {
            width: 100px;
            height: 100px;
            background-color: pink;
            float: left;
            margin-top: 50px;
        }
        
        .two {
            width: 200px;
            height: 200px;
            background-color: skyblue;
            float: left;
            /* 因为有浮动，不能生效 盒子无法水平居中 */
            margin: 0 auto;
        }
        
        .three {
            width: 300px;
            height: 300px;
            background-color: orange;
        }
    </style>
</head>
<body>
        <div class="two">two
        <div class="one">如果one是two的子集，会盖在two上</div>
        </div>
    <div class="three">three</div>
  
  
  <br><br>

    <div class="one">如果one和two是兄弟，两个人并列</div>
    <div class="two">two </div>
    <div class="three">three</div>
  
  
</body>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651029424787-ae043355-d77a-4e80-9331-5139c0063e93.png)

1.脱离标准流（脱标），在标准流中不占位置，相当于飘在空中 <br />2.浮动比标准流高半个级别，可以盖住标准流中的元素<br />3.浮动找浮动，父子关系：下一个浮动元素会盖在上一个浮动元素后面，兄弟关系：两个浮动元素并列<br />4.浮动的标签：顶对齐（脱离顶对齐加margin）<br />5.浮动有 特殊的显示效果<br />·一行可以显示多个<br />·可以设置宽高<br />6.浮动后的标签具备行内块特点：在一行排列，宽高生效<br />7.浮动的元素不能通过text-align：center或margin：0 auto居中
## 5.5 浮动布局注意点
浮动和标准流的父盒子搭配。（先用标准流父元素排列上下位置, 之后内部子元素采取浮动排列左右位置. ）<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650943715541-f48c587a-901d-42d3-8f60-ea1c32edc0d5.png)<br />	一个元素浮动了，理论上其余的兄弟元素也要浮动。

## 5.6 清除浮动
### 1）为什么需要清除浮动？
由于父级盒子很多情况下，不方便给高度，但是子盒子浮动又不占有位置，最后父级盒子高度为 0 时，就会影响下面的标准流盒子。<br />子元素浮动后脱标，不占位置。如果子元素浮动了，此时子元素不能撑开标准流的块级父元素。
### 2）清除浮动本质
清除浮动的本质是清除浮动元素造成的影响：浮动的子标签无法撑开父盒子的高度<br />	 如果父盒子本身有高度，则不需要清除浮动<br />	清除浮动之后，父级就会根据浮动的子盒子自动检测高度。<br />	父级有了高度，就不会影响下面的标准流了
### 3）清除浮动方法
#### ①给父元素加高度
（实际工作中有很多场景不方便加高度：新闻，电商）
#### ②额外标签法
在父元素内容的最后添加一个块级元素。给添加的块级元素设置：clear：both<br />缺点：在html里添加多余的标签
#### ③单伪元素清除法
（项目中常用）<br />用伪元素替代了额外标签<br />1.基本写法<br />.clearfix::after{<br />content:“''<br />display：block<br />clear：both}

补充写法：<br />为了兼容性，在后面添加<br />height：0；<br />visibility：hidden；
#### ④双伪元素清除法
/* .clearfix::before 作用：解决外边距塌陷问题 */<br />/* 外边距塌陷：父子标签，都是块级，子级加margin会影响父级的位置 */<br />.clearfix::before,<br />.clearfix::after{<br />content:'';<br />display:table;}<br />/* 真正清除浮动的标签 */<br />clearfix::after{<br />clear:both;}
#### ⑤给父元素设置：
overflow：hidden<br />优点：方便<br />缺点：无法显示溢出的部分<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651023727396-0b6dd71b-4017-431c-a2fc-337de5a67b68.png)

# 6. 定位
## 6.1 定位的作用
①让元素自由的摆放在网页的任意位置<br />②一般用于盒子之间的层叠情况
## 6.2 常见应用场景
①盒子与盒子之间的层叠<br />②让盒子始终固定在某个地方
## 6.3 基本使用
①定位方式<br />position：<br />相对relative<br />绝对absolute<br />固定 fixed

②设置偏移值<br />设置两个方式：水平，垂直方向<br />left+px<br />right<br />top<br />bottom

## 6.4 相对定位
相对自己之前的位置进行定位<br />不会改变标签的显示模式，块级还是块级<br />原<br />来在标准流的位置继续占有，后面的盒子仍然以标准流的方式对待它<br />相对定位并没有脱标

如果left和right都有，以left为准<br />top和bottom都有以top为准

## 6.5 绝对定位
绝对定位：先找已经定位的父级，如果有这样的父级就以这个父级为参照物定位(用relative比较多）<br />如果祖先元素有定位（相对、绝对、固定定位），则以最近一级的有定位祖先元素为参考点移动位置。

1.脱标，不占位<br />2.改变标签的显示特点：具备行内块的特点：加宽度高度生效，如果没有宽度也没有内容，盒子的宽度尺寸就是0

## 6.6 子绝父相
父级相对定位，子级绝对定位<br />（这里父级是上一级，绝对定位查找父级的方式，就近查找定位的父级，如果逐层查找不到这样的父级，就以浏览器窗口参照）

定位：子绝父相居中（宽度，水平居中）<br />绝对定位的盒子不能使用margin ：auto居中
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
   .box{
            /* 1.绝对定位的盒子不能使用margin ：auto居中 */
            position: absolute;
            /* margin: 0 auto; */
            /* left:50%，整个盒子移动到浏览器中线偏右 */
            left:50%;
            /* 把盒子向左侧移动：自己宽度的一半 */
            /* margin-left: -150px; */
            top: 50%;
            /* margin-top: -150px; */

            /* 自动计算   位移：自己高度的一半 */
            transform: translate(-50%,-50%);
            width: 400px;
            height: 300px;
            background-color: pink;
        }
    </style>
</head>
<body>
    <div class="box">

    </div>
</body>
```

 <br />①<br /> left:50%，整个盒子移动到浏览器中线偏右 <br /> 把盒子向左侧移动：自己宽度的一半 <br /> <br />②自动计算<br />位移：自己高度的一半transform：translate（-50%，-50%）



## 6.7 固定定位
相对于浏览器进行定位移动<br />position：fixed<br /> <br />1.脱标，不占位置<br />2.改变位置参考浏览器可视窗口，不随滚动条滚动<br />3.具备行内块特点

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651026506781-ac2b9773-ec93-4758-8ccf-98b32b51f7c7.png)

## 6.8 堆叠顺序
元素的层级关系<br />标准<浮动<定位<br /> <br />不同定位之间<br />相对、绝对、固定默认层级相同，<br />此时【html】（不是css）写在下面的元素层级更高，会覆盖上面的元素。 <br />默认情况下，定位的盒子，后来者居上

在使用定位布局时，可能会出现盒子重叠的情况。此时，可以使用 z-index 来控制盒子的前后次序 (z轴)<br />z-index 的特性<br />		属性值：正整数、负整数或 0，默认值是 0，数值越大，盒子越靠上；<br />		如果属性值相同，则按照书写顺序，后来居上；<br />		数字后面不能加单位。<br />注意：z-index 只能应用于相对定位、绝对定位和固定定位的元素，其他标准流、浮动和静态定位无效。
# 7. 元素的显示与隐藏
## 7.1 display
display: none 隐藏对象<br />display：block 除了转换为块级元素之外，同时还有显示元素的意思。<br />display 隐藏元素后，不再占 有原来的位置。（相当于直接从html里消失了）

## 7.2 visibility
visibility：visible ; 　元素可视<br />visibility：hidden; 　  元素隐藏<br />visibility 隐藏元素后，继续占有原来的位置（还能撑开一块空白的位置）

## 7.3 overflow 溢出（重点）
   overflow 属性指定了如果内容溢出一个元素的框（超过其指定高度及宽度） 时，会发生什么。<br />	visible: 不剪切内容也不添加滚动条<br />	hidden: 不显示超过对象尺寸的内容，超出的部分隐藏掉<br />	scroll: 不管超出内容否，总是显示滚动条<br />	auto: 超出自动显示滚动条，不超出不显示滚动条<br />	一般情况下，我们都不想让溢出的内容显示出来，因为溢出的部分会影响布局。<br />	但是如果有定位的盒子， 请慎用overflow:hidden  因为它会隐藏多余的部分

## 7.4 元素透明度
元素整体（包括内容）透明度<br />opacity：0~1的数字<br />0：完全透明<br />1：完全显示

# 8.精灵图与字体图标
## 8.1 精灵图
   为了有效地减少服务器接收和发送请求的次数，提高页面的加载速度<br />   将网页中的一些小背景图像整合到一张大图中 ，这样服务器只需要一次请求就可以了。<br />    这个大图片也称为 sprites  精灵图  或者 雪碧图<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651040952290-d142b700-8995-45d5-8ac8-8bf4a10dfe32.png)

### 1）使用精灵图
1.用span、b、i 等标签，转换为inline-block<br />2.设置标签宽高，和所需小图的尺寸一样<br />3.将精灵图设置为盒子的背景图background-position<br />4. 移动的距离就是这个目标图片的 x 和 y 坐标和左上角（0，0）之间的差距<br />5. 因为一般情况下都是往上往左移动，所以数值是负值。
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
      <style>
       span{
            display: inline-block;
            width: 18px;
            height: 24px;
            background-image: url(./images的副本/taobao.png);
            background-position: -3px 0;
        }
        b{
            display: block;
            width: 24px;
            height: 21px;
            background-image: url(./images的副本/taobao.png);
            background-position: 0 -90px;
        }
    </style>
</head>
<body>
    <span></span>
    <!-- 精灵图的标签都用 行内标签span、b、i -->
    <b></b>
</body>
```
### ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651041137731-95cdf082-c6a7-4f2f-bef7-be063f0d0bda.png)
### 2）总结
​	    1. 精灵图主要针对于小的背景图片使用。<br />		2. 主要借助于背景位置来实现---background-position 。<br />		3. 一般情况下精灵图都是负值。（千万注意网页中的坐标： x轴右边走是正值，左边走是负值， y轴同理。） 

## 8.2 字体图标
字体图标 iconfont ： 展示的是图标，本质属于字体<br />优点:1.灵活修改尺寸、颜色 <br />2.轻量，体积小、渲染快，降低服务器请求次数 <br />3.兼容性：几乎兼容所有主流浏览器

字体图标的下载<br />icomoon 字库 ： [http://icomoon.io](http://icomoon.io)<br />阿里iconfont字库：[http://www.iconfont.cn/](http://www.iconfont.cn/) <br />定制自己的字体图标：在ICONFONT上传svg矢量图
```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
  <link rel="stylesheet" href="./iconfont的副本/iconfont.css">
      <style>
          .iconfont {
            font-size: 100px;
        }
        
        i {
            color: brown;
        }
    </style>
</head>
<body>
    <i class="iconfont icon-favorites-fill"></i>
</body>
```
使用字体图标 <br />1.引入字体图标样式表 iconfont.css <br />2.调用2个类名class=“ iconfont  icon-xxx”
