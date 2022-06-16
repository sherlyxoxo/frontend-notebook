# 1. 屏幕尺寸
屏幕尺寸：屏幕对角线的长度，用英寸测量 <br />pc分辨率 <br />1.1920*1080 <br />2.1366*768 .... <br />缩放150% (1920/150%)*(1080/150%) 

物理分辨率（出厂） <br />逻辑分辨率（软件驱动决定的） <br />写代码要参考逻辑

分辨率 iphone6/7/8 <br />物理分辨率 750*1334 <br />逻辑分辨率 375*667 比例关系2：1<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651202646526-7e022d03-592f-4752-8c6c-370914d53be6.png)

# 2. 视口
视口（viewport）就是浏览器显示页面内容的屏幕区域<br />使用meta标签设置视口宽度，制作适配不同设备宽度的网页<br /><metaname="viewport"content="width=device-width, initial-scale=1.0">
# 3.移动端常见布局
## 3.1移动端单独制作
		流式布局（百分比布局）<br />		flex 弹性布局（强烈推荐）<br />		less+rem+媒体查询布局<br />		混合布局
## 3.2 响应式
		媒体查询<br />		bootstarp
## 3.3流式布局
		流式布局，就是百分比布局，也称非固定像素布局。<br />                宽度自适应，高度固定<br />		是移动web开发使用的比较常见的布局方式
# 4. flex布局
flex弹性布局 <br />浏览器提倡的布局模型 <br />布局网页更简单、灵活、避免浮动脱标的问题<br />为父盒子设为 flex 布局以后，子元素的 float、clear 和 vertical-align 属性将失效


## 4.1 组成部分
父元素添加display：flex，子元素可以自动的挤压或拉伸 <br />组成部分： 1.弹性容器flex 2.弹性盒子 3.主轴 交叉轴 （主轴：水平 默认侧轴垂直

## 4.2 flex-direction主轴方向
在 flex 布局中，是分为主轴和侧轴两个方向，同样的叫法有 ： 行和列、x 轴和y 轴<br />	默认主轴方向就是 x 轴方向，水平向右<br />	默认侧轴方向就是 y 轴方向，水平向下<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651203572137-5cc2eb62-1f0b-4f5e-98a7-f54693a0b15f.png)

主轴和侧轴是会变化的，就看 flex-direction 设置谁为主轴，剩下的就是侧轴<br />	属性值及含义<br />		row：默认值从左到右<br />		row-reverse：从右到左<br />		column ： 从上到下<br />		column-reverse：从下到上

```html
 <style>
        * {
            margin: 0;
            padding: 0;
        }

          li {
            list-style: none;
        }

        .box li {
            display: flex;
            /* 修改主轴的方向 */
            flex-direction: column;
            /* 视觉效果：垂直居中 */
            justify-content: center;
        
            align-items: center;
            width: 80px;
            height: 80px;
            border: 1px solid #ccc;
        }
        
        .box img {
            width: 32px;
            height: 32px;
        }
    </style>
</head>
<body>
    <div class="box">
        <ul>
            <li>
                <img src="./images/media.png" alt="">
                <span>媒体</span>
            </li>
        </ul>
    </div>
 </body>
```

## 4.3 justify-content 主轴对齐
```html
 <style>
        * {
            margin: 0;
            padding: 0;
        }

        .box {
            /* 视觉效果：子集水平排列 */
            /* 弹性盒子默认在主轴排列 */
           display: flex;
           /* 居中，无间距 */
           /* justify-content: center; */

           /* 间距在弹性盒子之间 */
           /* justify-content: space-between; */

           /* 所有地方的间距都相等 */
           /* justify-content: space-evenly; */

           /* 子级之间的距离是父级两头距离的2倍，（因为间距加在子级的两侧） */
           justify-content: space-around;
           
           
            height: 200px;
            border: 1px solid #000;
        }

        .box div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>
<body>
    <div class="box">
        <div>1</div>
        <div>2</div>
        <div>3</div>
    </div>
 </body>
```


flex- start 默认值从头部开始，如果主轴是x轴，则从左到右<br />	flex-end 从尾部开始排列<br />	center 在主轴居中对齐（如果主轴是x轴则水平居中）<br />	space-around  子级之间的距离是父级两头距离的2倍，（因为间距加在子级的两侧）<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651203572137-5cc2eb62-1f0b-4f5e-98a7-f54693a0b15f.png)<br />space-between 先两边贴边，再平分剩余空间（重要)<br />space-evenly所有地方的间距都相等

## 4.4 align-items侧轴对齐
```html
 <style>
      * {
            margin: 0;
            padding: 0;
        }
        
        .box {
            display: flex;
            /* 居中 */
            /* align-items: center; */
            /* 拉伸：默认值，现有状态，测试的时候要去掉子集高度 */
            /* align-items: stretch; */
            height: 300px;
            margin: auto;
            border: 1px solid #000;
        }
        
        .box div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
        
        .box div:nth-child(2) {
            align-self: center;
        }
    </style>
</head>
<body>
    <div class="box">
        <div>1</div>
        <div>2</div>
        <div>3</div>
    </div>
 </body>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651203771986-e54e199d-d90d-4eb1-9792-2f7d240b77a7.png)<br /> 添加到父级<br />1.flex-start <br />2.flex-end <br />3.center <br />4.stretch 默认值，弹性盒子沿着侧轴被拉伸至扑满容器 
## 4.5  flex-wrap换行
```html
 <style>
      * {
            margin: 0;
            padding: 0;
        }
        
         .box {
            display: flex;

            /* 默认nowrap不换行 */
            /* 换行 */
           flex-wrap: wrap;

           /* 调节行的对齐方式  */
           align-content: center;
           align-content: space-around;
           align-content: space-between;
          
           
            height: 500px;
            border: 1px solid #000;
        }
        
        .box div {
            width: 100px;
            height: 100px;
            background-color: pink;
        }
    </style>
</head>
<body>
    <div class="box">
        <div>1</div>
        <div>2</div>
        <div>3</div>
    </div>
 </body>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651217239082-5b9c3517-d8e5-4ffd-9807-fca14f556b12.png)

默认情况下，项目都排在一条线（又称”轴线”）上。<br />	flex-wrap属性定义，flex布局中默认是不换行的。<br />	nowrap 不换行<br />	wrap 换行
## 4.6 align-content换行后侧轴对齐
flex-start 默认值在侧轴的头部开始排列<br />flex-end 在侧轴的尾部开始排列<br />center  在侧轴中间显示<br />space-around 子项在侧轴平分剩余空间<br />space-between  子项在侧轴先分布在两头，再平分剩余空间<br />stretch 设置子项元素高度平分父元素高度

## 4.7 弹性子盒子
特点：不给宽高的时候，宽和内容一样 高和父级一样 <br />行内元素flex后变弹性盒子
### 1）flex属性
```html
 <style>
      * {
            margin: 0;
            padding: 0;
        }
        
       .box {
            display: flex;
            height: 300px;
            border: 1px solid #000;
        }

        .box div {
            height: 200px;
            margin: 0 20px;
            background-color: pink;
        }

        .box div:nth-child(1) {
            width: 50px;
        }

        .box div:nth-child(2){
            /* 占父集剩余尺寸的份数 */
            flex:4;
        }
        .box div:nth-child(3){
            flex: 2;
        }
    </style>
</head>
<body>
    <div class="box">
        <div>1</div>
        <div>2</div>
        <div>3</div>
    </div>
 </body>
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651203904289-5c6cd3b3-4008-48ef-8f1d-48a27f53b8fa.png#clientId=u0c7f50d9-10ae-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=304&id=ud3e9eb98&margin=%5Bobject%20Object%5D&name=image.png&originHeight=608&originWidth=1894&originalType=binary&ratio=1&rotation=0&showTitle=false&size=32505&status=done&style=stroke&taskId=u2b022590-c552-4744-83ad-ea7448564fe&title=&width=947)<br />使用flex属性修改弹性盒子伸缩比 <br />属性flex:值  数值（整数） <br />注意：只占用父盒子剩余尺寸的份数
## 2）align-self
控制子项自己在侧轴上的排列方式<br />属性允许单个项目有与其他项目不一样的对齐方式，可覆盖 align-items 属性<br />默认值为 auto，表示继承父元素的 align-items 属性，如果没有父元素，则等同于 stretch 

# 5. 移动适配
## 5.1 rem
rem是一个相对单位，类似于em，em是父元素字体大小<br />不同的是rem的基准是相对于html元素的字体大小<br />rem的优势：父元素文字大小可能不一致， 但是整个页面只有一个html，可以很好来控制整个页面的元素大小
```html
 <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        /* 1rem = 1html标签字号大小 */
        html {
            font-size: 20px;
        }
        
        .box {
            width: 5rem;
            height: 3rem;
            background-color: pink;
        }
```
rem：使用rem单位设置网页元素的尺寸 <br />网页效果：屏幕宽度不同， rem相对单位，相对html标签的字号计算结果 1rem=1html字号大小（根字号） html{ font-size} 
## <br />5.2 媒体查询
媒体查询：设置差异化css样式 <br />检测视口的宽度 html标签的字号为视口宽度的1/10 
```css
/* 移动适配 */
/* 1. HTML标签加字号 1/10; 2. 写rem单位的尺寸 */
 @media (width: 320px) {
    html {
        font-size: 32px;
    }
}
@media (width:375px) {
    html {
        font-size: 37.5px;
    }
}
@media (width: 414px) {
    html {
        font-size: 41.4px;
    }
} 

.box {
    /* 68 * 29 */
    /* width: 68px; */
    /* 设计稿375, HTML 37.5   68/37.5 */
    width: 1.813rem;
    height: 0.773rem;
    background-color: pink;
}

```
## 5.3 rem适配布局
rem适配原理 设计稿尺寸px  ÷ html标签字号（1/10视口宽度）<br /> flexible.js 根据不同的视口宽度给网页中html根节点设置不同的font-size<br />引入flexible.js文件<br /><scriptsrc="../js/flexible.js"></script>
# 6. less
使用less语法快速编译生成css 

less是css预处理器，后缀.less <br />浏览器不识别less代码，目前网页要引入对应的css文件
## 6.1 注释
//单行注释内容 快捷键 ctrl+/ <br />块注释/* */ 快捷键shift alt a<br />单行注释无法生成到css，只能在less查看
## 6.2 运算
加+减-乘* <br />除法<br />（/) <br />./ 
```less
.box {
    width: 100 + 10px;
    width: 100 - 20px;
    width: 100 * 2px;
    width: 100 + 2rem;
    width: 100./5rem;
    width: (100/2rem);

    // 除法
    width: (68 / 37.5rem);
    // height: 29 ./ 37.5rem;

    height: 29 / 37.5rem;

}
```
最后跟单位,不用打空格
## 6.3 嵌套
.父级选择器{ 样式 <br />.子集选择器{ 样式} } <br />&表示当前选择器 方便代码迁移
```less
.father {
    width: 100px;
    .son {
        color: pink;
        // & 表示当前选择器
        &:hover {
            color: green;
        }
    }

    &:hover {
        color: orange;
    }
}
```
## 6.4 变量
@变量名:值; @color: pink;<br />	必须有@为前缀<br />	不能包含特殊字符<br />	不能以数字开头<br />	大小写敏感	
```less
// 1. 定义. 
@colora:green;

@fontsize:12px;


// 2.使用
.box {
    color: @colora;
    font-size: @fontsize;
}

.father {
    background-color: @colora;
}

.aa {
    color: @colora;
}less导出css文件
单独导出
第一行//out: ./文件夹/

禁止导出
第一行//out: false
```
## 6.5 导入
less导入 (less文件，可以省略后缀.less）<br /> @import 空格'./ less';
```less
@import './01-体验less.less';
@import './02-注释';
@import './03-计算';

```
## 6.6 导出
less导出css文件 <br />单独导出 第一行//out: ./文件夹/ 

```less
// 重命名生成新文件
// out: ./qqq/daqiu.css 

// 直接导出本身
// out: ./abc/

.box {
    color: red;
}
.box{
    font-size: 16px;
}

@import './03-计算.less';
```
禁止导出 第一行//out: false
```less
// out: false
```
# 7. vw和vh
w/vh单位 <br />相对单位 相对视口的尺寸计算结果 <br />vw：viewport width <br />vh：viewport height <br />1vw：1/100视口宽度 <br />vw=px / （1/100视口宽度）<br /> vw和vh不要混用
```html
// out: ./
* {
margin: 0;
padding: 0;
}

// 68 * 29  -- vw
.box {
width: (68/3.75vw);
height: (29/3.75vw);
background-color: pink;
}

.box2{
width: (68/6.67vh);
height: (29/6.67vh);
background-color: green;
}

```
# 8. 响应式布局
## 8.1 响应式开发原理
	使用媒体查询针对不同宽度的设备进行布局和样式的设置<br />	设备的划分情况<br />		小于768的为超小屏幕（手机）<br />		768~992之间的为小屏设备（平板）<br />		992~1200的中等屏幕（桌面显示器）<br />		大于1200的宽屏设备（大桌面显示器）
## 8.2 媒体查询
max-width≤ <br />min-width ≥ 
```html
<style>
  /* 视口宽度小于等于768px， 网页背景色是粉色 */
  @media(max-width:768px){
    body{
      background-color: pink;
    }
  }
  
  /* 视口宽度大于等于1200px， 网页背景色是skyblue */
  @media(min-width:1200px){
    body{
      background-color: skyblue;
    }
  }
    </style>
```

书写顺序：注意层叠性 <br />min-width从小到大写 max-width 从大到小 
```html
<style>
  /*
  视口宽度 >= 768px，网页背景色是 粉色
  视口宽度 >= 992px，网页背景色是 绿色
  视口宽度 >= 1200px，网页背景色是 skyblue
  */
  
  /* css属性都有层叠性 */
  @media (min-width:758px) {
    
    body{
      background-color: pink;
    }
  }
  @media (min-width:992px) {
    
    body{
      background-color: green;
    }
  }
  @media (min-width:1200px) {
    
    body{
      background-color: skyblue;
    }
  }
    </style>
```
可写在引入css文件里link属性<br />media = “（）”
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 视口宽度 >= 992px，网页背景色为粉色 -->
    <!-- 视口宽度 >= 1200px，网页背景色为绿色 -->
    <link rel="stylesheet" href="./one.css" media="(min-width:992px)">
    <link rel="stylesheet" href="./two.css" media="(min-width:1200px)">
    
  </head>
  <body>
    
  </body>
</html>
```

完整写法：media 关键词 媒体类型 <br />关键词 and/only/not <br />媒体类型 screen/print 打印预览/speech阅读器 /all默认
## 8.3 响应式布局容器
	响应式需要一个父级做为布局容器，来配合子级元素来实现变化效果<br />	在不同屏幕下，通过媒体查询来改变这个布局容器的大小，再改变里面子元素的排列方式和大小<br />	父容器版心的尺寸划分<br />		超小屏幕（手机，小于 768px）：设置宽度为 100%<br />		小屏幕（平板，大于等于 768px）：设置宽度为 750px<br />		中等屏幕（桌面显示器，大于等于 992px）：宽度设置为 970px<br />		大屏幕（大桌面显示器，大于等于 1200px）：宽度设置为 1170px 

