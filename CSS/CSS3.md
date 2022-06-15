# 1. 过渡
让元素样式慢慢变化，常配合hover使用，增强网页交互体验 <br />transition 所有的属性都能过渡，过渡配合hover使用,谁变化谁添加<br />transition: 要过渡的属性  花费时间  运动曲线  何时开始;<br />	1：属性 ： 想要变化的 css 属性， 宽度高度 背景颜色 内外边距都可以 。如果想要所有的属性都变化过渡， 写一个all 就可以<br />	2：花费时间： 单位是 秒（必须写单位） 比如 0.5s <br />	3：运动曲线： 默认是 ease （可以省略）<br />	4：何时开始：单位是 秒（必须写单位）可以设置延迟触发时间  默认是 0s  （可以省略）<br />常用：transition: 属性（all） 时间 
```html
<style>
        变化前，加transition
        .box{
            width: 300px;
            height: 300px;
            background-color: pink;
            /* 宽度300-600，花费1s */
            /* 过渡配合hover使用,谁变化谁添加transition属性 */
            /* transition: width 1s, background-color  1s ; */
            /* 如果变化的属性多，直接写all代表所有 */
            transition: all 1s;
        }
  
        变化后，不加
        .box:hover {
            width: 600px;
            background-color: red;
        }
  </style>
```
# 2. 2D-平面转换
使用transform属性，实现元素的位移、旋转、缩放等效果， <br />改变盒子在平面内的形态：2d转换（位移、旋转、缩放） <br />正数向右下，负数向左上
## 2.1 translate位移
transform：translate（水平，垂直） <br />如果只给一个值，只在x轴移动 <br />单独设置，translateX（） translateY（）<br />1.数字+px<br />2.百分比，盒子自身尺寸的百分比<br />/* transform: translate(100%,50%); *
## 2.2 rotate旋转
	让元素在二维平面内顺时针或者逆时针旋转<br />	transform: rotate(角度deg)<br />	角度为正时，顺时针，角度为负时，逆时针<br />	默认旋转的中心点是元素的中心点<br />        旋转必须要有过渡属性
```html
<style>
   img {
            width: 250px;
            transition: all 2s;
        }
        
        img:hover {
            /* 顺 */
            transform: rotate(360deg);
            /* 逆时针 */
            /* transform: rotate(-360deg); */
        }
  </style>
```
## 2.3 transform-origin 改变转换原点
默认原点是盒子中心， <br />transform-origin：原点水平位置 原点垂直位置； /* 空格隔开 */<br />①方位名词(top、bottom、left、right、center)<br />②像素<br />③百分比（按照盒子自身尺寸）<br />默认旋转的中心点是元素的中心 (50% 50%)，等价于  center     center
## 2.4 位移+旋转
同时位移+旋转要用transform复合属性<br />不能单独写，不然会被层叠 <br />transform复合属性 ：translate（数值）rotate（数值）<br />不能先写rotate， 因为旋转会改变坐标轴向 <br />移动的距离要减去自身的宽度
## 2.5 scale 缩放
transform：scale（缩放倍数）<br />不用带单位<br />大于1表示放大，小于1表示缩小，等于1不变 <br />缩放和位置的关系很重要，先缩放还是先定位,否则会被层叠性影响，最好用复合属性一起写。<br />transform: translate(-50%, -50%) scale(1);<br />先写位置，再缩放，因为位置移动的数值可能和自身大小的百分比有关<br />scale（2,3）：逗号隔开，转变宽度为原来的大小的2倍，高度为原来大小3倍的。）
# 3. 3D转换
## 3.1 3位坐标
 x 轴：水平向右  -- 注意：x 轴右边是正值，左边是负值<br />	y 轴：垂直向下  -- 注意：y 轴下面是正值，上面是负值<br />	z 轴：垂直屏幕  --  注意：往外边的是正值，往里面的是负值<br />

 ![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651128709729-7a02014c-8b37-43ce-bcba-f916b366e638.png)

 <br />	z轴位置和视线相同

## 3.2 3D位移
语法： transform: translate3d(x, y, z)<br />/* 注意：x, y, z 对应的值不能省略，不需要填写用 0 进行填充 */<br />transform: translate3d(100px, 100px, 0)<br />单独写：<br />transform：translateX <br />transform：translateY <br />transform：translateZ<br />单独写z轴看不见效果,要用perspective属性，实现透视效果

## 3.3 perspective视距
3D透视 - perspctive<br />- 透视也称为视距，所谓的视距就是人的眼睛到屏幕的距离；<br />- 距离视觉点越近的在电脑平面成像越大，越远成像越小；<br />

![img](https://cdn.nlark.com/yuque/0/2022/png/27972378/1651128861865-48636e6a-f908-493b-9aa8-208c5392a483.png)<br />- 透视的单位是像素；<br />	透视需要写在被视察元素的父盒子上面<br />	perspecitve 给父级进行设置，translateZ 给 子元素进行设置不同的大小<br />       近大远小，正大负小 加给父级，perspective:值（800-1200px之间)

## 3.3 3D旋转
3D旋转 - rotate3d(x, y, z)<br />	transform: rotateX(45deg) -- 沿着 x 轴正方向旋转 45 度<br />	transform: rotateY(45deg) -- 沿着 y 轴正方向旋转 45 度<br />	transform: rotateZ(45deg) -- 沿着 z 轴正方向旋转 45 度<br />	transform: rotate3d(x, y, z, 45deg) -- 沿着自定义轴旋转 45 deg 为角度

左手法则：判断旋转方向：左手握住旋转轴，拇指指向正值方向，手指弯曲方向为旋转正值方向。
## 3.4 3D呈现 - transfrom-style
	控制子元素是否开启三维立体环境<br />	transform-style: flat  代表子元素不开启 3D 立体空间，默认的<br />	transform-style: preserve-3d 子元素开启立体空间<br />	代码写给父级，但是影响的是子盒子
## 3.5 空间缩放
空间缩放 transform：scaleX（倍数)<br /> transform：scaleY（倍数) <br />transform：scaleZ（倍数) <br />transform：scale3d（,,,)
# 4. 动画 animation
多个状态间的变化过程，过程可控（重复播放、最终画面，是否暂停)<br />最小单元：帧或动画帧
## 4.1 定义动画
写在style里<br />@keyframes 动画名称 {<br />from{ } <br />to{} <br />}

@keyframes 动画名称 {<br />0%{ } 10%{ } 15%{ } 100%{ } <br />}<br />(百分比指的是动画时长占比）
```html
<style>
  /* 一、定义动画：从200变大到600 */
        @keyframes change {
            from{ width: 200px;}
            to{width: 600px;}
        }

        /* 二、定义动画：200，500*300，300*800 */
        @keyframes change {
            0%{width: 200px;}
            50%{width: 500px;
            height: 300px;}
            100%{
                width: 300px;
                height: 800px;
            }
  </style>
```

1.可以做多个状态的变化 keyframe 关键帧<br />2.里面的百分比要是整数<br />3.里面的百分比就是总的时间的划分
## 4.2 使用动画-拆分写法
必写：<br />①animation-name: 动画名称;<br />②animation-duration: 持续时间；<br />③animation-timing-function：<br />	速度曲线细节 : 规定动画的速度曲线，默认是`ease`<br />	linear  从头到尾的速度是相同的。匀速<br />	ease  默认。动画以低速开始，然后加快，在结束前变慢<br />	steps() 指定了时间函数中的间隔数量（步长）<br />④animation-delay  规定动画何时开始，默认是0 ;<br />⑤animation-iteration-count  规定动画被播放的次数，默认是1，还有 infinite<br />⑥animation-direction  规定动画是否在下一周期逆向播放，默认是“ normal" alternate 逆播放<br />⑦animation-play-state 规定动画是否正在运行或暂停。默认是 running，还有" paused"<br />⑧animation-fill-mode 规定动画结束后状态，保持 forwards  回到起始 backwards
## 4.3 使用动画-复合属性
选择器{<br />animation：动画名称 动画时长   (必写）<br />速度曲线   steps（数字）分步动画 <br />延迟时间 重复次数 动画方向 执行完毕画面; }<br />简写属性里面不包含  animation-paly-state

注意：取值不分先后 如果有2个时间，第一个时间表示动画时长，第二个表示延迟时间
```html
<style>
   .box {
            width: 200px;
            height: 100px;
            background-color: pink;
            /* animation: change 1s linear; */
            /* 分步动画 */
            /* 3: 重复3次播放 */
            /* animation: change 1s steps(3) 1s 3; */
            /* 无限循环 */
            animation: change 1s infinite alternate;
            /* 默认值, 动画停留在最初的状态 */
            /* animation: change 1s backwards; */
            /* 动画停留在结束状态 */
            /* animation: change 1s forwards; */
        }
  
   .box:hover{
            animation-play-state: paused;
        }
        
        @keyframes change {
            from {
                width: 200px;
            }
            to {
                width: 600px;
            }
        }
  </style>
```
## 4.4 精灵动画
精灵图动画-逐帧动画 <br />1.准备显示区域 定宽高盒子,和一张小图尺寸一样，背景图为当前精灵图 <br />2.定义动画 改变背景图的位置，移动的距离就是精灵图的宽度 <br />from-to <br />(动画当中的开始状态和盒子的默认样式相同的，可以省略from）<br />3.使用动画 添加速度曲线steps（N），N与精灵图上小图个数相同 <br />添加无限重复效果
## 4.5 多组动画
多组动画 animation： 动画1， <br />动画2；<br />无缝动画要重复最开始的一部分
