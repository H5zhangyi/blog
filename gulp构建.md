gulp学习心得：(可供新手参考)
========================

#1.全局安装gulp
npm install --global gulp

#2. 作为项目的开发依赖（devDependencies）安装：(在项目根目录操作)
npm install --save-dev gulp

#3.在项目根目录创建一个gulpfile.js文件（此文件名不可更改）

#4.初始化生成package.json (可以先用默认配置)
npm init

接下来就是安装各种组件了。。。
  官网搜索安装就行

gulp官网：http://www.gulpjs.com.cn/
npm组件官网：https://www.npmjs.com/

下面贴出一个常用的配置(仅供参考)：

*************************************************************
package.json
*************************************************************

{
  "name": "qmcz",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "dependencies": {
    "gulp": "^3.9.1"
  },
  "devDependencies": {
    "gulp-autoprefixer": "^3.1.1",
    "gulp-clean": "^0.3.2",
    "gulp-clean-css": "^2.0.13",
    "gulp-concat": "^2.6.0",
    "gulp-connect": "^5.0.0",
    "gulp-inject": "^4.1.0",
    "gulp-less": "^3.1.0",
    "gulp-manifest": "^0.1.1",
    "gulp-rev": "^7.1.2",
    "gulp-sequence": "^0.4.6",
    "gulp-uglify": "^2.0.0",
    "gulp-watch": "^4.3.10"
  },
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}

*************************************************************
gulpfile.js
*************************************************************

var gulp = require('gulp');  // 基础库
var less = require('gulp-less');  // less编译成css
var autoprefixer = require('gulp-autoprefixer');  // 兼容代码自动补全
var cleanCss = require('gulp-clean-css');  // css代码压缩
var concat = require('gulp-concat');  // 代码合并
var uglify = require('gulp-uglify');  // js代码压缩
var watch = require('gulp-watch');  // 监听
var connect = require('gulp-connect'); // 构建本地服务

// 解决浏览器缓存问题，增强用户体验
var rev = require('gulp-rev');  // 以md5方法重命名文件
var manifest = require('gulp-manifest'); // 用json文件保存文件名
var inject = require('gulp-inject'); // 更换html文件引用路径
var clean = require('gulp-clean');  // 删除文件
var sequence = require('gulp-sequence'); // 保证文件执行顺序

gulp.task('less',function(){
	return gulp.src(['view/*.less'])
		.pipe(less())
		.pipe(autoprefixer({
			browsers: ['last 20 versions'],
			cascade: true
		}))
		.pipe(cleanCss())
		.pipe(concat('index.min.css'))
		.pipe(gulp.dest(''))
});

gulp.task('js',function(){
	return gulp.src(['config/config.js','controller/*Controller.js'])
		.pipe(uglify())
		.pipe(concat('index.min.js'))
		.pipe(gulp.dest(''))
});

gulp.task('mywatch',function(){
	// gulp.watch('view/*.less').on('change',function(e){
	// 	console.log("less编译"+e.path);
	// });
	gulp.watch(['view/*.less'],['less']);
	gulp.watch(['config/config.js','controller/*Controller.js'],['js']);
});

gulp.task('localhost',function(){
	return connect.server({
		root: '',  //静态资源目录
		port: 8000
	});
});

// 解决浏览器缓存(开发阶段可暂时不用)
gulp.task('rev',function(){
	return gulp.src(['index.min.css','index.min.js'])
		.pipe(rev())
		.pipe(gulp.dest(''))
		.pipe(rev.manifest())
		.pipe(gulp.dest('data/'));
});

gulp.task('inject',function(){
	return gulp.src('index.html')
		.pipe( inject( gulp.src(['index-*.min.css','index-*.min.js']) ))
		.pipe( gulp.dest('') );
});

gulp.task('clean',function(){
	return gulp.src('index-*.min.*')
		.pipe( clean());
});

gulp.task('build',function(cb){
	return sequence('clean','rev','inject',cb);
});

gulp.task('default',['mywatch','localhost','build']);
