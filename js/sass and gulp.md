###一、SASS
>css和html不属于编程语言没有变量，函数，循环，判断....
>优势：有编程语言的语法，可以简化代码量

>写中文的时候scss是不能识别的需要定义编码方式
>scss文件中再去写注释的时候必须使用/**/
>公共类（样式）
sass
>1.定义变量
````scss
    $color:red;

    .p1{
        color:$color;
    }
````
>2.定义公共部分
/*定义部分*/
.名字{
	样式集合
}

/*导入部分*/
@extend .名字;
````scss
    .public{
        width:800px;
        height:30px;
        line-height:30px;
    }

    nav{
        @extend .public;
        border:1px solid  red;
    }

    nav-pro{
        @extend .public;
    }
````

>3.嵌套
````scss
.content{
    width: 800px;
    height: 300px;
    
    .content-left{
        float: left;
        
        a{
            text-decoration: none;
            
           &:hover{
            color: yellow;
           }
        }  
    }
    .content-right{
        float: right;
    }
}    
````


>4.函数
````scss

/*
  参数  键值对
 $width:300px
 */
/*定义函数*/
@mixin 函数名($变量:默认值,$变量:默认值...){
   width: $width;
   height: $height; 
}
//导入
@include 函数名(实参);

/*（1）有默认值*/
@mixin pub($width:500px,$height:600px){/*若没传参 则是默认值*/
    width:$width;
    height:$height;
}

.content{
    @include pub(800px,900px);  /*自己传了参数*/
    .content-left{
        float:left;
        a{
            text-decoration:none;
            &:hover{
                color:red;
            }
        }
    }
}

/*（2）无默认值*/

@mixin pub($width,$height){/*形参*/
    width:$width;
    height:$height;
}

.content{
    @include pub(400px,500px);  /*实参*/
    .content-left{
        float:left;
        a{
            text-decoration:none;
            &:hover{
                color:red;
            }
        }
    }
}
````

>5.判断
````scss
@mixin test($condition){
  $color: if($condition,blue,red);
  color:$color;
}

.First{
  @include test(true); /*blue*/
}
.Second{
  @include test(false); /*red*/
}

/*例如：*/
$flag:false/true;
@if $flag {
    .div{
        color: red;
       }
    }
    
@else { 
    .div{
        color: pink;
    }
}
````

>6.循环
/*循环*/
````scss
@for $i from 1 through 5
{
    .border-#{$i}
    {
        width:#{$i * 100}px;
    }
}
````
>css中的结果
```css
    .border-1 {
  width: 100px;
}

.border-2 {
  width: 200px;
}

.border-3 {
  width: 300px;
}

.border-4 {
  width: 400px;
}

.border-5 {
  width: 500px;
}
```



---
###二、gulp

>默认去安装了NODE
>node -v 查看node版本
>npm -v查看npm 版本号
>npm install xx.xx.x  安装某个插件/框架
>项目的依赖环境
>>生产依赖   （项目部署上线也需要）  dependencies
>>开发依赖   （在开发阶段需要的）  devDependencies

>1.项目基于npm进行管理  会默认生成一个package.json的文件
>npm init  项目初始化
>>package name:给这个文件起名字（符合命名规范）不能起中文(首字母不能大写)，默认不起名字，直接回车它的名字是当前项目的名字

###gulp
>前段自动构件化工具  （gulp  webpack）

>一
>>1.项目初始化git init -y

>>2.npm install gulp@3.9.1 -g(全局安装gulp）

>>3.npm install gulp@3.9.1 --save-dev（-save-dev下载到开发依赖）

>>4.自己在devDependencies配置你需要的插件名称及版本

>>5.npm install（跑环境根据package.json)

>>6.在当前项目下 gulp -v 查看版本号

>二  基于gulp进行编译

>>1.gulp的所有操作都是基于gulpfile文件的（js文件）

>>2.在gulpfile文件中想要用到我们gulp模块或者gulp插件必须先导入
let gulp = require("模块名称");

>>3.执行gulp任务  默认任务直接 gulp   gulp 任务名






