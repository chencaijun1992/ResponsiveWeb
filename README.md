#响应式开发的概念及其学习
## 响应式开发
1. 用于改变布局
2. 通过媒体查询(medium query)进行页面重构：
	* 在小屏幕上扩大链接的目标区（更好遵循触摸屏的**费茨定律**） 
	* 对某些元素有选择的显示或者隐藏，优化导航功能
	* 设置**响应式排字法**，渐进改变字体大小和行距

##旧版浏览器中媒介查询的支持
1. 2007年JQuery的插件有限媒体查询，针对链接最小宽度和最大宽度
2. 近期推出的css3-mediaquries.js
3. 老版本浏览器处理`media="only screen and (min-width:401px) and (max-width:600px)"`,会解析为`media="only"`，忽略后面的内容
4. 

##未来技术
1. 流动网格(fleible grid layout)，弹性图片(flexible image)，媒体查询(media queries)

>响应式网站是一个设计理念，是多项技术的综合体（不是单纯的自适应布局，弹性布局等概念）

##响应式网站的优点
1. 减少工作量
  * 网站、设计、代码、内容都只需要一份
  * 多出来的工作是对js，css的改动
2. 节省时间
3. 每个设备都能得到正确的设计

##响应式网站的缺点
1. 会加载更多的样式和脚本资源
2. 设计比较难精确定位和控制
3. 老版本浏览器兼容性较差

##浏览器一览
1. Statcounter分区域统计浏览器用户量

##响应式网站设计实现原则
1. progressive enhancement 渐进增强

2. graceful degrdation 优雅降级
3. 不管设备大小，都显示一样的内容
4. 断点的选择
	* 0-480小屏幕
	* 481-800 中屏幕
	* 801-1400大屏幕
	* 1400+超大屏幕


##如何组织项目目录结构
*  


## 3-1
1. html lang="zh-CN"
2. `<meta charset="utf-8">`
3. `<meta http-equiv="x-ua-compatible" content="ie=edge">
`代表IE的兼容模式，`ie=edge`表示以最新的IE浏览器模式渲染界面
4.`<!--[if lt IE8]-->
<p></p>

<!--[end if]-->` `lt`表示如果你的浏览器版本小于IE8,`lt`还可以改成gt(大于),gte（大于等于）,lte(小于等于)

##HTML5新标签
```

<header>
</header>

<footer></footer>

<!--导航-->
<nav></nav>
<!--article和section都是语义化标签,对于一段主题性的内容，则就适用 section，而假如这段内容可以脱离上下文，作为完整的独立存在的一段内容，则就适用 article。-->
<article></article>
<section></section>
<!--仅仅使文字醒目,不一定重要-->
<b></b>
<!--文字是醒目且重要的-->
<em></em>
<!--有差异的-->
<i></i>

```

## Class和ID命名
class表样式，命名时使用中横线分隔如`class="top-head"`
id一般用于js区分标签等。

##必不可少的图片用`<img>`,可有可无的使用`styles`


##没有标题的section定义为div（可有可无）

## Css resets统一各个浏览器的差异，让所有浏览器按照同样的规则进行解析代码,但是
* Css resets还是继承链不好调试,
* Css重置所有样式，而Normalize.css则是该重置的重置，该保留的保留



##黑色一般设置为`color:#222`（偏深灰，现在的设计不使用纯黑，降低对比度）

## px,em,rem
* em 相对的长度单位
 * em相对参照物为父元素的font-size
 * em具有继承的特点
 * 当没有设置font-size的时候，浏览器会有一个默认的em设置：1em=16px
 * em缺点：容易混乱
 
* rem
 *  相对参照物为根元素html，相对参照物固定不变，所以比较好计算
 * 当没有设置font-size的时候，浏览器会有一个默认的rem设置，1em=16px,这里和em一致

## flex布局可以替代浮动等

##清楚浮动：
* `<div style="clear:both">`
*  overflow: auto;

* 现在使用的方法

```
	.clearfix:after{
		content:".";
		display:block;
		height:0;
 		clear:both;
 		visibility:hidden;
 
 	}
 	兼容IE6，IE7
 	.clearfix{
 		zoom:1;
 	}
 	
```

## BFC概念( Box、Formatting Context)
 * 哪些属性可以触发BFC：
 如：
 ```
 display:block;
 display:table-cell;
 display:inline-block;
 position:fixed;
 position:absolute;
 background-color:#ccc;
 ```

##尼古拉斯大师的改进方案
这段代码的`height:0 visibility:hidden`就是为了隐藏元素
```
.clearfix:after{
		content:".";
		display:block;
		height:0;
 		clear:both;
 		visibility:hidden;
 
 	}
```
可以改成匿名表格单元
```
.clearfix:after,.clear:before{
	content:"";
	display:table;
	clear:both;

}
.clear:before：为了清除margin-top,bottom 叠加,不写也可以
```

##中文版chrome中如果使用line-height=3rem会转成36px，（中文字体大小有下限，低于12px就会使用默认最小12px,英文是10px）

##inline-block之间会有间隙(原因是html代码中的空白符导致的，比如回车换行)
* 可以将回车换行去掉
* 将父节点的font-size设置为0（会引入副作用：出现padding-bottom,要重新知道子元素font-size）
* li标签重写成这样
* li标签不闭合
* 设置父边距`margin-left=-3px`（有的浏览器显示不一样）
> 目前还没有可以完美解决的办法


##Css sprite 

## 使得图标变灰色
* 增加滤镜：使用filter,但是有时候IE可以识别，Chrome不能识别（使用
	`-webkit-filter:grayscale(100%)`）
* 不需要自己去记，可以通过[autoprefixer](http://autoprefixer.github.io)这个网站，输入css之后自动加前缀。

## 媒体查询单位
* @media的优先级比较高，是在html样式执行前就会执行的，所以`1rem=16px`使用的是默认值

## CSS选择器
* 基本选择器
	* 所有元素，如`div *`
	* 元素选择器，如`div a `
	* `.class`
	* `#id`
	*  后代选择器
	*  `>`子元素选择器（直接子元素）
	*  `+`相邻元素选择器（选中与其相邻的后一个元素）
	*  `~`通用兄弟元素选择器（选中后面所有的元素）
* 属性选择器
	* `E[attr]`如`a[href]`
	* `E[attr='value']`如`a[href="www.baidu.com"]`
	* `E[attr*'value']`
	* `E[attr^='value']`以某种开头（有点像正则）
	* `E[attr$='value']`以某种结尾（有点像正则）
	* `E[attr~='value']`包含该属性
	* `E[attr|='value']`和`^`类似但是这个选择器还可以包括`/`
* CSS3选择器:nth-child和:nth-of-type的差别
	* 看一个例子`p:nth-child(2)`指的是父元素的第二个子元素，并且子元素类型是`p`才会选中，如果不是`p`则没反应
	* `p:nth-of-type(2)`指的是父元素的第二个类型为`p`的子元素，只要父元素有第二个类型为`p`的子元素，必然能找到

## 好的图片滚动插件
* 支持不同数量的图片
* 支持响应式布局
* 具有良好的兼容性
* 可以加入其它参数等
* [OwlCarousel](https://github.com/OwlFonk/OwlCarousel)
* Zepto：移动端Jquery


## 怎样挑选第三方组件
* 使用人数
* 是否开源
* 文档是否齐全
* 活跃性
* 轻量级

## 使用表格进行响应式设计
* 很多列的表格在中小屏幕显示的比较丑
	* 隐藏表格中不重要的列
	* 行列倒置
	* 使用表单摞起来

## 响应式图片
> 加载与用户设备相匹配的小图片，即快速，又不会影响用户的体验

* 图片的排版与布局
* 对应不同的设备大小进行图片匹配（增加了UI设计师的工作量）

## 如何实现响应式图片
* js或者服务端
* srcset
* srcset配合sizes
	* sizes(媒体查询，) 
* picture (对IE浏览器完全不兼容，但是有个picturefill可以解决这个问题)，在引入`<script src="js/vendor/picturefill.min.js"></script>`之后，使用`picture`方法如下

```
  <div class="item">
                <picture>
                    <source srcset="img/ad001-l.png" media="(min-width:50em)">
                    <source srcset="img/ad001-m.png" media="(min-width:30em)">
                    <img src="img/ad001.png" alt="2015">
                </picture>
            </div>
```
* svg（illustrator，或者[在线svg生成](http://editor.method.ac/)）

## 使用polyfill(填平浏览器兼容间隙的想法/脚本)
* [picturefill库](http://scottjehl.github.io/picturefill/) 这个库可以对不支持picture属性的IE浏览器使用js获取`srcset`和媒体查询的一些设置，再通过js来设置输出什么样的图片
* 

## 图片进行压缩
[tinypng](https://tinypng.com/)


## Node.js
* npm的使用
	* npm init 创建一个全新的package名称
	* dependencies生产环境的依赖
	* devDependecies `^包版本`依赖的版本大于等于该版本
	* 修改`pakage.json`的依赖后可以使用`npm i`或者`npm install`按照json里规定的依赖包
	* `npm install --save`将依赖添加到生产环境中去
	* `npm install --save-dev`将依赖添加到开发环境中去
* node启动server服务
	* `sudo npm isntall http-server -g` 
	* `http-server src`指定路径
	* `control + c`终止服务
	*  [github:http-server](https://github.com/indexzero/http-server) 


## 如何处理兼容性
* 通用处理方法：**CSS Hack**
	* [browserhacks](http://browserhacks.com/)
* Polyfill 如[Respond](https://github.com/scottjehl/Respond)用来使得IE6-8支持媒体查询
* shiv 如[html5shiv](https://github.com/aFarkas/html5shiv)，使得IE8以下能支持HTML5的元素
* modernizr 主动检测浏览器是否支持新特性[modernizr](https://modernizr.com/)

## 移动设备测试
* 企业级测试[testin](http://testin.cn/)
* 安卓虚拟机不推荐使用eclipse中的,推荐[genymotion](http://www.genymotion.net/)

## 多个设备上进行调试
* 省时的浏览器同步测试工具[browsersync](http://www.browsersync.cn/)
* 简单使用
	
	> 安装 BrowserSync
	>
	npm install -g browser-sync
	>
	// --files 路径是相对于运行该命令的项目（目录） 
browser-sync start --server --files "css/*.css


## 发布网站前要进行代码优化
* 压缩
	* 手工代码压缩[css js压缩](https://javascript-minifier.com/) 
* 打包发布主流的3个工具
	* 	自动化构建工具：
		*  Grunt
		*  Gulp
	* 	静态资源打包工具
		*  WebPack  

* 合并
* 增加版本号

## Gulp的简单使用
### 来看一个使用gulp执行一个任务的例子
1. 安装`sudo npm install gulp --save-dev`
2. 新建`gulpfile.js`用来保存gulp的任务,

	```
		var gulp= require('gulp');

		gulp.task('hello',function () {
   		console.log("hello");
		});

	```

3. 运行任务`gulp hello`


### 为了使用gulp打包，必须安装的一些插件
`sudo npm install gulp-rev gulp-rev-replace gulp-useref gulp-filter gulp-uglify gulp-csso --save-dev 
`

* **[gulp-rev](https://github.com/sindresorhus/gulp-rev)**：发布新的版本号的时候，给每个文件计算一个哈希码，修改掉文件名字（标识文件是否发生更改）
* **[gulp-rev-replace](https://github.com/jamesknelson/gulp-rev-replace)**：文件名改变了，对应的引用也要发生变化
* **[gulp-useref]()**：在我们的html中可以通过注释的方法写一些设置，比如根据这样的注释

``` 
    <!-- build:css css/combined.css -->
    <link href="css/one.css" rel="stylesheet">
    <link href="css/two.css" rel="stylesheet">
    <!-- endbuild -->
```
就能合并这两个css文件到一个文件combined.css中去

```
    <link rel="stylesheet" href="css/combined.css"/>

```
* **gulp-filter**筛选和恢复文件流
* **gulp-uglify**压缩js代码的主要插件
* **gulp-css**压缩css代码的主要插件
* `/*! */`的注释不会被压缩，可用来声明版权
* **来看一段gulpfile代码：**

```
var gulp= require('gulp');
var rev =require('gulp-rev');
var revReplace=require('gulp-rev-replace');
var useref=require('gulp-useref');
var filter=require('gulp-filter');
var uglify=require('gulp-uglify');
var csso=require('gulp-csso');

gulp.task('default',function () {
    var cssFilter=filter('*/*.css',{restore:true});
    var jsFilter=filter('*/*.js',{restore:true});
    var indexHtmlFilter=filter(['**/*','!**/index.html'],{restore:true});
    return gulp.src('src/index.html')
        .pipe(useref())
        .pipe(jsFilter)
        .pipe(uglify())
        .pipe(jsFilter.restore)
        .pipe(cssFilter)
        .pipe(csso())
        .pipe(cssFilter.restore)
        .pipe(indexHtmlFilter)
        .pipe(rev())
        .pipe(indexHtmlFilter.restore)
        .pipe(revReplace())
        .pipe(gulp.dest('dist'))
});


```
* 其他插件如`gulp-watch`监听文件改变、`gulp-postcss`为css文件添加一些前缀、`gulp-concat`合并js、`gulp-responsive`生成响应式的图片


## WebStorm使用技巧
* 常用快捷键
	* `control+M`找闭合标签
	* `alt+shift+上下`交互代码位置
	* 插入下一行`shift + enter`,插入上一行`alt+shift+enter`
	* 回到上次编辑的地方`command+shift+退格键`
* 定位到图片
	* `control+ space +space`
* 图片预览宽高
	*  `shift`悬浮光标到src中去
* 点击色块出现拾色器
* 标签，变量等重命名`control +T`右击可以`exinclude`
* 报错信息提示：按住`f2`切换错误位置，按`alt + enter`可以出现错误提示
* `Commoand + Mouse`调节代码区大小，如果不能就要设置这个选项`Editor->General->Change Font Size with Command + Mouse Wheel`

### 多光标功能
* 同时修改多个光标位置的内容(不对齐的话Reformat code`command+ALT+L`)，如

```
 <div class="item"></div>
 <div class="item"></div>
 <div class="item"></div>
 <div class="item"></div>
 <div class="item"></div>
```

###Emmet
[Emmet](http://docs.emmet.io/)是大幅度提高前端开发效率的一个工具,
主要用到的是这5个字符`>` `+` `^` `*` `()`来生成标签，使用`.` `#` `[]` 命名`$` 内容`{}`

* 生成无意义的文本`lorem5`后面跟着的数字表示无意义单词的数量
* 注意事项：
	* 不要加空格
	* 光标在末尾按`tab`键才能不全 

* css中的Emmet书写
   * 写`w`按`tab`，输出`width:`
   * 写`m10`按`tab`,输出`margin:10px`

 
## 流行的响应式框架
 * Bootstrap
 * Foundation
 * Semantic UI
 * Pure.css
 * 使用框架的缺点：
 	* 体积大，使用起来不方便
 	* 样式单调，没有创新 
 	* 大多数只适合做后台管理系统	
 
##产品经理的设计工具
* 草图绘制：mockup
* 原型设计：Axure
* 原型设计&UI设计：Sketch

## PS切图
* 选择切片选项->编辑切片选项直接设置宽高
* 文件->存储为web所用格式->选择图片保存格式：
	* 有动画的选择只能是`gif`
	* 对于没有动画的，颜色比较少，需要透明的，选择`GIF`|`PNG 8位`
	* 对于颜色比较多，需要透明的，选择`PNG 24位`
	* 对于不需要透明，颜色比较多的，选择`JPEG`

## Sketch


## 交互设计工具
* Flinto for mac
* Principle

 
  
