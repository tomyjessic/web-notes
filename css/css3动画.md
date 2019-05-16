2019.03.25  整理

******

# Css3动画课程

##transition过度效果

**兼容性**	

IE10+、谷歌、火狐、欧朋、safari

**相关属性**	

#### transition 简写属性  哪个元素需要过度加在哪个元素下面	

### 一、transition-property规定用于参与css过度的具体属性###

#### transition-property:all |none|property####

#### 注意：

1.若没设置transition-property属性，那么标签的所有属性默认都参与过度

2.如果让所有属性都参与过度，则可用**all** 

3.若需要transition-property属性，但又都不参于过度效果，则可用**none**

4.若设置的是具体属性，但本属性中没设置某个属性过度，则没参与过度的属性就没效果

### 二、transition-duration 参与过度属性的过渡时间

单位：s|ms 秒/毫秒

### 三、transition-timing-function 过渡效果时间曲线，默认ease

属性值：

​	cubic-bezier:具体的贝塞尔曲线值

可参考网址：**http://cubic-bezier.com/#.26,.84,.87,.11**

​	linear 类似匀速

​	ease 慢--快--慢   默认

​	ease-in  结束快  加速

​	ease-out 结束慢  减速

​	ease-in-out  慢--快--慢  开始和结束慢  比ease还慢

### 四、transition-delay  延迟

**作用：**	在指定的时间之后执行效果

**单位:**	s||ms

### 简写 ###	

transition: property,duration,timing-function,delay

**特殊写法**	transition: 1s width 2s,2s height,3s background-color;

​		1s:宽度执行时间    2s延迟2秒执行1s时间效果

# Css3 2D#

**相关属性**

### 一、transform: 2D/3D 之间的转换###

### 二、transform-origin: 更改元素的基点###

**相关属性值**

​	**translate(x,y)**	 **移动**	 沿着x,y移动元素

​	**scale(x,y)**	         **缩放**	 将宽度缩放x倍，高度缩放y倍 只写了一个值 表示宽高缩放倍数一样

​	**rotate()**                    **旋转**  可更改基点   angle角度  eg：30deg   旋转30度

​	**skew(x-angle,y-angle)**       **倾斜**	 如果里面有文字 文字也会一起倾斜







2019.3.26

# CSS 3D 和CSS 动画



首先，来复习一下`css3 2d`的内容。

## CSS3 3D

**相关属性**:

- transform:2d/3d之间的转换
- transform-origin:更改元素的基点
- transform-style:flat|preserve-3d 开启3d空间   哪个元素需要开启2D/3D空间就在其父元素上加入此属性
- perspective    景深,一般值的范围在900px-1200px ,景深的值最好不要太夸张
- perspective-origin 景深基点  调整基点看的角度就不同
- backface-visibility   背面隐藏



相关属性值：

- translateX | translateY | translateZ | translate3d(x,y,z)
- scaleX | scaleY | scaleZ | scale3d()
- rotateX(angle) | rotateY(angle) | rotateZ(angle)



## 景深

> 更多的时候是用在父元素的身上。

示例:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        section {
            width: 400px;
            height: 400px;
            border: 1px solid red;
            margin: 100px auto;
            /*一定要设置在父元素的身上*/
            perspective: 300px;
        }
        div {
            width: 100px;
            height: 100px;
            background-color: lightblue;
            transition: 1s;
        }

        section:hover div {
            transform: rotateX(45deg);
        }
    </style>
</head>
<body>
    <section>
        <div></div>
    </section>
</body>
</html>
```



## 开启3D空间

**transform-style:flat|preserve-3d 开启3d空间**

当属性值为`flat`的时候，网页是默认为`2d`空间的。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        section {
            width: 600px;
            height: 400px;
            border: 2px solid lightcoral;
            margin: 200px auto;
            background-color: lightblue;
            /*如果没有开启3d空间，那么效果就只是一个平面*/
            transform-style: preserve-3d;
            perspective: 400px;
            transition: 2s;
        }

        section div {
            width: 100px;
            height: 100px;
            background-color: lightgreen;
            transition: 2s;
        }
        section:hover {
            transform:rotateY(85deg);
        }
        section:hover div {
            transform: translateZ(100px);
        }
    </style>
</head>
<body>
    <section>
        <div></div>
    </section>
</body>
</html>
```



## 示例： 正方体



中午练习：scaleZ()



## rotate3d(x,y,z,a)

x：是一个0到１之间的数值，主要用来描述元素围绕X轴旋转的矢量值；
y：是一个０到１之间的数值，主要用来描述元素围绕Y轴旋转的矢量值；
z：是一个０到１之间的数值，主要用来描述元素围绕Z轴旋转的矢量值；
a：是一个角度值，主要用来指定元素在3D空间旋转的角度，如果其值为正值，元素顺时针旋转，反之元素逆时针旋转。 





## **3D缩放**：

CSS3 3D变形中的缩放主要有scaleZ()和scale3d()两种函数，当scale3d()中X轴和Y轴同时为1，即scale3d(1,1,sz)，其效果等同于scaleZ(sz)。通过使用3D缩放函数，可以让元素在Z轴上按比例缩放。默认值为１，当值大于１时，元素放大，反之小于１大于0.01时，元素缩小。

*scale3d(sx,sy,sz)*

 sx：横向缩放比例；
 sy：纵向缩放比例；
 sz：Z轴缩放比例；

*scaleZ(s)*

s：指定元素每个点在Z轴的比例。 
**注：scaleZ()和scale3d()函数单独使用时没有任何效果，需要配合其他的变形函数一起使用才会有效果**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        section {
            width: 400px;
            height: 400px;
            border: 2px solid lightseagreen;
            perspective: 300px;
            transform-style: preserve-3d;
        }
        div {
            width: 100px;
            height: 100px;
            background-color: lime;
            transition: 8s;
        }
        section:hover div {
            transform:rotateX(720deg) scale3d(1.2,2.1,3);
        }
    </style>
</head>
<body>
    <section>
        <div></div>
    </section>
</body>
</html>
```

## translate3d

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <style>
        .stage {
            width: 300px;
            height: 300px;
            float: left;
            margin:15px;
            position: relative;
            background: url("./img/bg.jpg") repeat center center;
            perspective: 1200px;
        }

        .container {
            position: absolute;
            top:20%;
            left:50%;
            transform-style: preserve-3d;

        }

        .container img {
            position: absolute;
            margin-left:-70px;
            margin-right:-100px;
        }

        .container img:nth-child(1) {
            z-index:1;
            opacity: .6;
        }

        .s1 img:nth-child(2) {
            z-index:2;
            transform:translate3d(30px,30px,200px);
        }


        .s2 img:nth-child(2) {
            z-index: 2;
            transform: translate3d(30px,30px,-200px);
        }



    </style>
</head>
<body>
<div class="stage s1">
    <div class="container">
        <img src="./img/k2.png" alt="" width="70" height="100">
        <img src="./img/k2.png" alt="" width="70" height="100">
    </div>
</div>

<div class="stage s2">
    <div class="container">
        <img src="./img/k2.png" alt="" width="70" height="100">
        <img src="./img/k2.png" alt="" width="70" height="100">
    </div>
</div>


</body>
</html>
```



## 动画 animation

Animation是一个简写属性，包含以下内容：

1、Animation-name    调用关键帧

2、Animation-duration   设置完成时间

3、Animation-timing-function   动画的速度曲线

4、Animation –delay                   延迟

5、Animation-iteration-count   动画应该播放的次数

​	N  设置播放次数    infinite   无限次播放  

6、Animation-direction        规定是否该轮流反向播放动画

​	Normal   alternate   动画应该轮流反向播放

7、Animation-play-state              暂停/运行

​	Paused  暂停

​	Running  运行

8、Animation-fill-mode   规定动画在播放之前或者之后，其动画效果是否可见

​	None  不改变默认

​	Forwards  当动画完成后保持最后一个属性值

​	Backwards  在Animation –delay指定的一段时间之内，在动画显示之前，应用开始属性值。

​	Both  向前和向后填充模式都被应用。

简写语法：

Animation: name duration timing-function delay  iteration -count  direction



**关键帧语法**:



```
@keyframes 关键帧的名字 {
    0% {}
    30% {}
    50% {}
    100%{}
}

@keyframes 关键帧的名字 {
    from {}
    to{}
}
```





​                                                                                                                                                                                                 





