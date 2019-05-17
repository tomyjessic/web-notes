1.项目初始化
npm init -y
2.gulp 全局
npm install gulp -g
3.当前项目下
npm instsll gulp --save--dev
4.gulp 插件  package.json文件中dependencies里写入
5.npm install
6.gulp -v 查看gulp是否安装上 版本号


>默认去安装了NODE
>node -v 查看node版本
>npm -v查看npm 版本号
>npm install xx.xx.x  安装某个插件/框架
>项目的依赖环境
>>生产依赖   （项目部署上线也需要）  dependencies
>>开发依赖   （在开发阶段需要的）  devDependencies

>1.项目基于npm进行管理  会默认生成一个package.json的文件
>npm init  项目初始化  (自已一项一项设置，生成package.json文件 )
>
>>package name:给这个文件起名字（符合命名规范）不能起中文(首字母不能大写)，默认不起名字，直接回车它的名字是当前项目的名字

>npm init -y 默认设置  （一次生成package.json文件，已配置好）


###gulp
>前端自动构件化工具  （gulp  webpack）

###gulp
1.配置清单
npm init -y   

>将gulp安装到全局(MAC下安装不成功需要在命令之前加sudo)
npm install gulp -g(全局)

>在当前项目下安装gulp
npm install gulp --save-dev

>gulp插件
>>gulp-sass  将sass转为css
>>gulp-cssmin  css压缩
>>gulp-uglify  js压缩
>>gulp-concat  文件合并
>>gulp-rename   文件重新命名
>>gulp-imagemin  图片压缩


>>一般在项目中间项目从git上拉下来之后做的一件事就是跑环境
>> npm  install (就会自动找到项目清单package.json)把依赖的开发环境，生成环境都下载下来

###gulp中的方法
>在当前目录下执行gulp看下信息必须配置文件gulpfile.js

>在gulpfile下引入gulp

//引入gulp模块
var gulp = require("gulp");

//配置一个默认任务task
//第一个参数：任务名称   第二个参数当前任务依赖其它任务   第三个参数：回调函数
````javascript
gulp.task("default",["say","dance"],function(){//命令行默认的去找
	console.log("别惹我");
});
````

//布置某一个任务
```javascript
gulp.task("say",["dance"],function(){
	console.log("say任务执行");
});

gulp.task("dance",function(){
	console.log("say任务执行");
});
```



//src(); 源文件路径 dest();目标文件路径  pipe();管道方法，表示下一步
//布置任务  将src目录下的index.html复制到pipe()目录下


gulp.task("copyHTML",function(){
	return gulp.src("src/index.html").pipe(gulp.dest("dest"))
});

gulp.task("copyCss",function(){
	return gulp.src(["src/*.css","lib/*.css"]).pipe(gulp.dest("dest"));
});

gulp.task("cpyAll",function(){
	return gulp.src("lib/*").pipe(gulp.dest("dest/all"));
});

gulp.task("all",function(){
	return gulp.src("lib/*/**").pipe(gulp.dest("dest/all"));
});

//布置任务：监听src下的index.html文件 如果有改动自动复制到dist目录下
gulp.watch("witchHTML",function(){
	//当前那个文件改变  监听按个任务
	return gulp.watch("src/index.html",["copyHTML"]);
});



//直接安装  npm install --save-v 
//转为css
gulp.task("sass",function(){
	return gulp.src("src/style.scss")
	.pipe(cssmin())
	.pipe(gulp.dest("dist"));
});
//压缩
gulp.task("sass",function(){
	return gulp.src("src/style.scss")
	.pipe(cssmin())
	.pipe(gulp.dest("dist"));
});

//重命名
gulp.task("sass",function(){
	return gulp.src("src/style.scss").
	pipe(cssmin()).
	pipe(rename("style.min.css"))
	.pipe(gulp.dest("dist"));
});
//压缩js并重新命名
gulp.task("uglify",function(){
	return gulp.src("src/style.scss").
	pipe(cssmin()).
	pipe(rename("style.min.css"))
	.pipe(gulp.dest("dist"));
});

//将所有css文件合并成一个
gulp.task("concat",function(){
	return gulp.src(["1.css","2.css","3.css"]).
	pipe(concat("all.css")).
	pipe(gulp.dest("dist"));
});


// 压缩图片
gulp.task("imgmin",function () {
    return gulp.src("src/img1/*.jpg").
        pipe(imagemin()).
        pipe(gulp.dest("src/img2"));
});




