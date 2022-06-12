# 1.基础概念


## 1.1 网页与网站

网站由网页构成<br>
网页内容包括：文字、图片、连接等元素  
网页是使用 html 超文本标记语言写的  
文件后缀名是 .html  



## 1.2 浏览器与浏览器内核

渲染引擎（浏览器内核）

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650356324636-331229bb-99f9-4746-83f0-fba709bface4.png)



## 1.3 web标准

![](https://cdn.nlark.com/yuque/0/2022/jpeg/27972378/1650356591333-34bf5c71-37cd-46dd-8426-a0ffdebf1554.jpeg)
### 1）结构-HTML
结构用于对网页元素进行整理和分类
### 2）表现-CSS
表现用于设置网页元素的版式、颜色、大小等外观样式，主要指的是CSS
### 3）行为-JavaScript
行为是指网页模型的定义及交互的编写



# 2.基本结构



## 2.1 语法规范

标签都使用<>包裹  
大部分成对出现，是双标签，单个出现是单标签  
标签由父子(包含)关系和兄弟(并列)关系  

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650358252285-83825eb3-cb2b-42f0-96c2-fcbf65f32d34.png)



## 2.2 基本结构（骨架标签）
![](https://cdn.nlark.com/yuque/0/2022/jpeg/27972378/1650358909192-522484f9-1c25-4c33-ba72-bfce0bbcb567.jpeg)
```html
<html>
  <head>
    <title>网页标题</title>
  </head>
  <body>
    网页内容
  </body>
</html>
```


## 2.3 骨架代码 （部分）

```html
<!DOCTYPE html> 
<!--文档类型声明标签，告诉浏览器这个页面采取html5版本来显示页面-->
<html lang="en">
  <!--告诉浏览器或者搜索引擎这是一个英文网站，本页面采取英文来显示-->
  <!--zh-CN简体中文/en英文-->
<head>
    <meta charset="UTF-8">
<!-- 字符集  采取UF-8来保存文字。如果不写就会乱码-->
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
     <!-- 网页兼容性 IE/EDGE差 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!--移动端网页开发 -->
  <title>Document</title>
</head>
<body>
    
</body>
</html>
```
字符编码 <meta charset="UTF-8"> 
标识网页使用的字符编码  
UTF-8万国码：所有被认证国家的语言 （GB2312:6000+汉字 GBK：20000+汉字）   
开发中统一使用UTF-8字符编码即可  



## 2.4 SEO三大标签

search engine optimization   
搜索引擎优化 让网站在搜索引擎上排名靠前  
方法   
1.竞价排名  
2.将网页制作成html后缀   
3.标签语义化（在合适的地方使用合适的标签）  

### 1）三大标签 

1.title：网页标题标签   
2.description : 描述  
3.keywords ：关键词  

```html
<!DOCTYPE html> 
<html lang="en">
<head>
   <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!-- meta:desc -->
  <!-- meta:kw -->
    <meta name="description" content="京东JD.COM-专业的综合网上购物商城，为您提供正品低价的购物选择、优质便捷的服务体验。商品来自全球数十万品牌商家，囊括家电、手机、电脑、服装、居家、母婴、美妆、个护、食品、生鲜等丰富品类，满足各种购物需求。">
    <meta name="keywords" content="网上购物,网上商城,家电,手机,电脑,服装,居家,母婴,美妆,个护,食品,生鲜,京东">
    <title>京东(JD.COM)-正品低价、品质保障、配送及时、轻松购物！</title>
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>
<body>
    
</body>
</html>
```
### 2）ico图标
link：favicon 自动 把这个图标放在根目录里，命名必须是favicon.ico  
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651043820309-c14852e7-cdca-449e-baa3-7db0d89ac960.png)



## 2.5 标签语义

根据标签的语义，在合适的地方给一个最为合理的标签，可以让页面结构更清晰。
### 1）html5 语义标签
手机端网页用，双标签，有利于浏览器的搜索引擎搜索  
1.header  网页头部  
2.nav  网页导航   
3.footer 网页底部  
4.aside 网页侧边栏  
5.section 网页区块  
6.article 网页文章  



# 3.常用标签

## 3.1 h系列-标题标签
```html
<h1>1级标题</h1>
<h2>2级标题</h2>
<h3>3级标题</h3>
<h4>4级标题</h4>
<h5>5级标题</h5>
<h6>6级标题</h6>
```
## ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650360718883-af0d20fc-4470-44d2-b79d-fa0bea2e044c.png)

h1-h6 字号逐级递减  
特点：自动换行、加粗  



## 3.2 \<hr>水平线

```html
 <h1>这是文章标题</h1> <hr>
   <p>阿卡贝拉（意大利：Acappella )即无伴奏合唱。 <br>
```
特点：单标签，自动换行
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650361083344-fdb25b70-fb6d-4784-80d2-d1f75b30746f.png)





## 3.3 p标签-段落标签

	浏览器会自动适应换行
```html
 <h1>这是文章标题</h1> <hr>
   <p>阿卡贝拉（意大利：Acappella )即无伴奏合唱。 <br>
     其起源可追溯至中世纪的教会音乐，当时的教会音乐只以人声清唱，并不应用乐器。<br>
    音频示例： 阿卡贝拉《千与千寻》阿卡贝拉（意大利：Acappella )即无伴奏合唱。其起源可追溯至中世纪的教会音乐，当时的教会音乐只以人声清唱，并不应用乐器。音频示例： 阿卡贝拉《千与千寻》阿卡贝拉（意大利：Acappella )即无伴奏合唱。其起源可追溯至中世纪的教会音乐，当时的教会音乐只以人声清唱，并不应用乐器。音频示例： 阿卡贝拉《千与千寻》</p>

    <p>“翻唱”是指将已经发表并由他人演唱的歌曲根据自己的风格重新演唱，包括重新填词，编曲。现在已有不少明星，都在翻唱他人的歌，不断在翻唱中突破自己，给大家带来不一样的风格。视频示例： 有一种悲伤（翻唱）-《A Kind of Sorrow》</p> 
```
# ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650361286066-85cd69f3-7ab1-4e8f-8e20-24a95302c392.png)

特点：段落间存在间隙，独占一行



## 3.4 换行标签\<br>

特点：强制换行，单标签  
（可以叠加，越多行距越大）  

```html
 <h1>这是文章标题</h1> <hr>
   <p>阿卡贝拉（意大利：Acappella )即无伴奏合唱。 <br>
     其起源可追溯至中世纪的教会音乐，当时的教会音乐只以人声清唱，并不应用乐器。
     <br><br><br><br><br> 
并不应用乐器。音频示例： 阿卡贝拉《千与千寻》阿卡贝拉（意大利：Acappella )即无伴奏合唱。其起源可追溯至中世纪的教会音乐，当时的教会音乐只以人声清唱，并不应用乐器。音频示例： 阿卡贝拉《千与千寻》</p>

```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650361779933-d40a8e37-2822-4fdc-bbe5-96c5e7ca6204.png)



## 3.5 文本格式化标签

```html
  <!-- 无语义-->
    <b>加粗</b>
    <i>倾斜</i>
    <u>下划线 </u>
    <s>删除</s> 
    
   <!-- 有语义-->
    <strong>加粗</strong>
    <ins>下划线</ins>
    <em>倾斜</em>
    <del>删除</del>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650421514245-2bd77855-26d1-4c29-a3ca-c92afd6e798f.png)
特点：语义-突出重要性的强调语境（便于浏览器理解)



## 3.6 布局标签

无语义-span、div  
特点：双标签、不含语义  
div：自动换行，一行只显示一个（块级元素）  
span：一行可显示多个（行内元素）  



## 3.7  图片标签 img
特点：单标签 
```html
<img src="./cat.gif" title="这是title文字，鼠标悬停的时候显示" width="300">
<img src="cat1.gif" alt="这是一只猫" border = 3>
<!--alt：替换文本，当图片不显示的时候就会显示替换文本 -->
```
### ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650426308471-72d694d2-ad37-4f83-8d54-caaa0076ea2e.png)
### 1） 属性
src: 图片的路径（来源）  
alt：当图片加载错误时显示的文字  
title:当鼠标悬停在图片上显示的文字（不仅图片可以提示，别的标签如a标签加上title也可以提示文字）  
width:图片的宽度  
height：图片的高度  
①只设置其中一个的时候，另一个会按比例缩放  
②两个都设置的时候，可能会变形  
border:图片的边框    
### 2） 属性特点
1.属性之间不分先后顺序，都写在标签里<>  
2.属性名与属性值之间以键值对的形式存在 ：关键词 = "值"  
3.数字值不需要加单位  
4.属性之间用空格隔开  



## 3.8 音频标签

```html
 <audio src="./music.mp3" controls autoplay loop></audio>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650504998039-f1e34db5-a3c3-402e-9af4-ba572fdf1bf7.png)

特点:双标签  
属性：  
src=“插入音频文件的地址”，相对路径  
controls 无值，如果声明了该属性，浏览器将提供一个包含声音，播放进度，播放暂停的控制面板，让用户可以控制音频的播放。  
autoplay 【音频】自动播放(部分浏览器不支持)  
loop 循环播放  
音频标签目前支持3种格式：mp3，wav，ogg  



## 3.9 视频标签

```html
    <video src="./video.mp4" controls autoplay muted loop></video>
```
特点和属性值与audio相似  
可设置weight和height  
autoplay： 【视频】谷歌浏览器要打上muted，实现静音播放  
视频标签目前支持3种格式：mp4，webM，ogg  



## 3.10 路径和链接

### 1） 路径
#### ①相对路径
从当前文件开始出发，找目标文件
![](https://cdn.nlark.com/yuque/0/2022/jpeg/27972378/1650435288625-3636cb28-24ea-4370-8087-bd5d52a126f1.jpeg)

```html
    <h2>同级</h2>
    <img src="cat.gif" alt="">
    <img src="./cat.gif" alt="">
    <h2>下级</h2>
    <img src="images/cat.gif" alt="">
    <h2>上级</h2>
    <img src="../DAY3/images/car.jpg" alt="">
```
#### ②绝对路径




### 2）链接标签  a

```html
     外部标签
    <a href="https://www.baidu.com" target="_blank">跳转到百度</a> <br> 
    内部标签
    <a href="./01-标题标签.html" target="_self">点击跳转到内部html文件</a><br>
    <a href="#">空链接，点击后刷新页面</a>
```
属性：
href:指定跳转的页面  
title：鼠标悬停显示的文字  
target:    窗口的打开方式： _self(默认会覆盖原来的窗口)   _blank(会以新的窗口打开)    
#：会阻止页面跳转但是会刷新页面



### 3）锚点链接

1.设置跳转链接使用#   
2.目标标签id值与连接#号后面一致  
```html
     <h1>武林外传</h1>
    <a href="#juqing"><h3>1.剧情简介</h3></a>
    <a href="#fenji"><h3>2.分集剧情</h3></a>
    <img src="图片/001.jpeg" width="800"/>
    
    <h4 id="juqing">剧情简介</h4> 
    <p>以掌柜的<a href="佟湘玉.html">佟湘玉</a>（抠门至极的女店主，风情万种但心地善良，婆婆妈妈又十分鸡贼）为首的一个客栈班底，这其中有跑堂的白展堂（会点穴、有武功，是个盗贼，想改过自新，其实胆小如鼠），有打杂的郭芙蓉（她自恃有武功，乱闯江湖，喜欢动手动脚，虽为大侠千金，其实武功不咋的，是个标准的野蛮女友），有厨子李大嘴（成天幻想学武功当大侠，就是不好好做饭），会算账的吕秀才（常常是子曰不离口，其实是个百无一用的书生，手无缚鸡之力却歪打正着地混来一个“关中大侠”的称号），有寄宿客栈的祝无双（虽为葵花派门人，其实是个常受欺负的弱女子，美丽却没有爱情光顾），有顽皮少女莫小贝（江湖上传闻是个女魔头，实际上是个爱逃学并且只想吃糖葫芦的小丫头片子），还有两位捕快，一个老邢，一个小六，每天梦想着破大案子，一身正气但却没有什么本事，却不知真正的大盗就在身旁……     </p>
    
    <h4 id="fenji">分集剧情</h4>
&nbsp;&nbsp;1 郭女侠怒砸同福店，佟掌柜妙点迷路人 

<p>一个月黑风高的杀人夜，传说中的雌雄双煞从天而降，打乱了同福客栈的安稳日子。家世显赫、从小娇生惯养的郭芙蓉，父亲是一代大侠，始终把她笼罩在阴影之下。从小争胜好胜的她，毅然选择了一条离家出走独闯江湖的路，却在第一站，被扣在了同福客栈，从此开始了艰苦卓绝的杂役生涯……</p>

```


## 3.9 注释和特殊字符

### 1）注释
<!--我是注释-->  
编辑器使用Ctrl+/ 快捷键  
### 2）特殊字符 （字符实体）
在网页中展示特殊符号效果时，需要 用字符实体替代。
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650438027386-f11cdd7d-3cff-438c-8ccf-108b9c93f9eb.png)



# 4. 表格

## 4.1 标签
```html
     <table>
       <caption>学生成绩单</caption>
       <thead>
           <tr>
        <th>姓名</th>
        <th>成绩</th>
        <th>评语</th>
            </tr>
        </thead>
        <tbody>
        <tr>
            <td>小哥哥</td>
            <td>100分</td>
            <td>good</td>
        </tr>
        <tr>
            <td>小姐姐</td>
            <td>excellent </td>
            <td>excellent </td>
        </tr>

        </tbody>
        <tfoot>
            <tr>
            <td>郭德纲</td>
            <td>140分</td>
            <td>140分</td>
            </tr>
        </tfoot>
                
    </table>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650505921587-f2016048-6dd7-4705-af4e-748d0bb8b0a8.png)



![](https://cdn.nlark.com/yuque/0/2022/jpeg/27972378/1650506386901-c61a3ae5-1d95-4fc8-b3c0-38b43cc17a23.jpeg)







\<table>\</table> 表格    
\<tr>\</tr> 行    
\<td>\</td> 单元格  
\<th>\</th> 表头    加粗  加黑 自动居中  
（th标签写在 tr标签内部，th=第一行的td，但语义更清晰）    
\<caption>\</caption>  表格的大标题   写在内部  显示外部  居中     

可写可不写，突出表格的不同部分，使语义更加清晰    
\<thead>\</thead>  结构头  
\<tbody>\</tbody>  结构体  
\<tfoot>\</tfoot> 结构底  
对table添加的属性只改变tbody，不改变thead和tfoot  



## 4.2 属性
**在table开始标签里写，属性=“数字” 不用加单位**
border:表格的边框   默认的0  
width：宽度  
height：高度  
align: left/center/right  
注意： 当给表格设置居中整个表格会居中（文字不会居中）      

当指定tr  或者td  文字居中  
colspan: 列合并   
rowspan：行合并      



```html
       <table border="1" width="500" height="500" align="center">
        <caption> <strong><h1>学生成绩单</h1> </strong></caption>
        <thead>
            <tr>
                <th>姓名</th>
                <th>成绩</th>
                <th>评语</th>
            </tr>
        </thead>
        <tbody>
            <tr align="center">
                <td>小哥哥</td>
                <td rowspan="2">100分</td>
                <td>good </td>
            </tr>
            <tr>
                <td>小姐姐</td>
                <td>excellent </td>
            </tr>

        </tbody>
        <tfoot>
            <tr>
                <td>郭德纲</td>
                <td colspan="2">140分</td>
            </tr>
        </tfoot>
    </table>
```


![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650507400312-2b493f4d-91a3-4344-9c83-3c1ec795f2d7.png)



### 合并单元格
1.明确合并哪几个单元格  
2.通过左上原则，确定保留谁，删除谁  
3.给保留的单元格设置，跨行合并rowspan，或跨列合并，colspan  
4.在\<td>标签里 写   
\<td rowspan=“合并的个数">  
5.不能跨结构合并 ，只能在thead中，或在tbody中，或在tfoot中  
		   
# 5. 列表
## 5.1 无序列表
ul表示无序列表的整体，  
li表示每一项（ul只能包裹li,li可以包括其他标签）  
特点：自动换行，自带圆点  
```html
     <ul>
        <li>榴莲</li>
        <li>香蕉</li>
        <li>苹果</li>
    </ul>
```
# ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650507920461-2ed07f90-a83c-4195-a0d6-c681cc2596b5.png)


## 5.2 有序列表

ol表现有序列表的整体，li表示每一项   
特点：自动换行，自带序号  

```html
     <ol>
       <li>张三：100</li> 
       <li>李四：80</li>
    </ol>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650508335098-7e488c84-8f17-45be-9de0-1cae92efc8fc.png)



## 5.3 自定义列表

dl表现自定义列表的整体，里面只能有dd和dt  
dd默认显示缩进  
dt表示自定义列表的主题，dd表示每一项内容。  
```html
   <dl>
        <dt>帮助中心</dt>
        <dd>账户管理</dd>
        <dd>用户指南</dd>
    </dl>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650508473101-ff3ef368-faf1-4d98-9df0-5c9b9341e43a.png)



# 6. 表单 

## 6.1 input-type属性
```html
    文本库: <input type="text" placeholder="请输入文字"> <br><br>
    密码框: <input type="password" placeholder="请输入密码"><br><br>
    单选框:
    <input type="radio"><br><br>
    多选框:
    <input type="checkbox"><br><br>
    上传文件:
    <input type="file"><br><br>

    提交:
    <input type="submit"><br><br>
    重置:
    <input type="reset"><br><br>
    按钮:
    <input type="button" value="按钮"><br><br>
```
input系列标签，特点：单标签，不会自动换行

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650509568544-61a80d72-fad7-4145-898d-8ba4348bb98b.png)

①text：文本框，用于输入单行文本  
②password：密码框，用于输入密码  
**（value=“文本框里实际存在的内容”**
**占位符，placeholder="提示文字"，文本框里实际不存在内容）**

③radio：单选框，用于单选  
④checkbox：多选框，用于多选  
⑤file：文件选择，用于之后上传文件  

⑥submit：提交按钮，用于提交  
⑦reset：重置按钮，用于重置  
（需要配合form表单才有作用）
⑧button：普通按钮，默认无功能，需要配合js添加功能  

其他type属性值  



![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651042117148-13cedf5d-25d2-46f2-b5b8-fc307b318541.png)



## 6.2 input单选框

1.在网页中显示多选一的表单控件  
2.type属性值：radio  
**①name：分组，有相同name属性值的单选框为一组，一组中同时只能有一个被选择**  
(name 属性用于对提交到服务器后的表单数据进行标识，或者在客户端通过 JavaScript 引用表单数据。  
**注释：**只有设置了 name 属性的表单元素才能在提交表单时传递它们的值。)  
**type="radio" name="命名为一组"**  

**②checked，默认选中**  
**type="radio" checked**  
```html
 性别
    <input type="radio" name="sex" >男
    <input type="radio" name="sex" checked>女
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650510632245-a1f9023d-8d43-4a12-9c72-85bb95262709.png)



## 6.3  **input其他属性**

required  表单拥有该属性表示其内容不能为空，必填  
autofocus 自动聚焦属性，页面加载完成自动聚焦到指定表单  
autocomplete  off /on  当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示出在字段中填写的选项  
默认已经打开，如 autocomplete="on“，关闭 autocomplete="off" 
需要放在表单内，同时加上name属性，同时成功提交  
multiple 可以多选文件提交  
```html
  <input type="file" multiple>
```


## 6.4 input按钮

**如果需要实现submit、reset按钮功能，需要form标签，包裹全部的表单标签**  
**属性value="给按钮添加名字"**  
```html
   <form action="">
    用户名：<input type="text" name="" id=""><br><br>
    密码：<input type="password" name="" id="">  <br><br>
    <input type="submit" value="免费注册">
    <input type="reset" name="" id="">
    <input type="button" value="普通按钮">
</form>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650512090333-3fcbc1cb-2ab3-43b6-9d65-83eae75f7f79.png)





## 6.5 button按钮和input按钮的区别

特点：双标签，可以包裹其他内容，文字，图片  
也和input一样有type属性值submit、reset  
但也需要form标签包裹才能生效  
```html
  <form action="">
        <input type="text"><br><br>
        <button type="submit">提交按钮</button>
        <button type="reset">重置按钮</button>
        <button>普通按钮，没功能</button>
    </form>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650534696718-5360a4c5-b845-4729-850c-ee220de01cd5.png)



## 6.6 表单-下拉菜单

特点：双标签  
select标签：下拉菜单的整体  
option：下拉菜单的每一项（选项名称不能写在value里）  
属性值  
selected 默认选中，写在option里，没点开菜单就能显示，点开已被选择  
```html
 <select name="" id="">
        <option value="">北京</option>
        <option value="">上海</option>
        <option value="" selected>广州</option>
        <option value="">深圳</option>
    </select>
```
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650534971003-164502cc-564e-468f-9d44-dbd8ca6e6e2d.png)



![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650535015486-4163f1e6-a08c-4eee-9bea-93e5962b0072.png)

## 6.7 文本域 textarea
特点：双标签，可以输入多行内容，随着内容自动撑开  
属性  
cols=“"  文本域内可见 宽度  
rows=“" 文本域内可见行数  
textarea 里标签设置maxlength=”字符上限“  

```html
 <textarea name="" id="" cols="30" rows="10" maxlength="30"></textarea>
```
# ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650595203498-1f69cdce-fb3b-45cb-b9e3-50eaa9420e12.png)
## 6.8 label标签
特点：双标签，绑定内容与表单标签的关系（点击文字也能选中单选框或复选框）
![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1650595485545-fa03d754-18c9-41bc-af7f-ffaec39d152e.png)

```html
 性别：
   <input type="radio" name="sex" id="nan"> <label for="nan">男</label>

   <label > <input type="radio" name="sex" >女</label>
```

方法①  
1）使用label标签把文本 包裹起来  
2）input里id属性，和label里的for属性设置成一样  

方法②  
1）直接用label把内容全部包裹起来  
**（单独捆绑，不能捆绑全部）**  
2）把label里的for删除  

## 6.9 form表单
主要的作用：是收集用户信息   发送后台  
action：  提交后台的地址   
method="get/post"   提交（传输）后台的方式  
name =“a” 告诉服务器  由哪个表单提交过来的  

