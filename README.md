gulp 快速入门 ![](https://img.shields.io/npm/l/whistle.svg?style=flat-square) 
=== 

> 基于流的自动化构建工具

<!-- TOC -->

- [API](#api)
- [gulp 的使用](#gulp-的使用)
    - [复制文件](#复制文件)
    - [复制多个文件](#复制多个文件)
    - [插件使用](#插件使用)
- [常用插件](#常用插件)

<!-- /TOC -->

<br>

## API
gulp 只有四个 API , task 用来创建任务，src 用来读取文件，watch 用来监视文件，dest 用来输出文件。还有用到 node 中的 pipe 方法，pipe 方法返回目标流的引用，这样就可以对流进行链式地管道操作。
- `gulp.task(name[, deps], fn)`
- `gulp.src(globs[, options])`
- `gulp.watch(glob[, opts], tasks)`
- `gulp.dest(path[, options])`

<br>
<br>

## gulp 的使用

1. 安装 gulp 
```
$ npm install --save-dev gulp
```

<br>

2. 配置到 package.json
```json
"scripts": {
    "build": "gulp"
  },
```

<br>

3. gulp 命令默认执行文件名为 gulpfile.js 的文件,我们可以在项目根目录下创建一个名为 gulpfile.js 的文件。
```javascript
var gulp = require('gulp')

gulp.task('default', function() {
    console.log('hello world')
});
```

<br>

4. gulp 默认执行的任务为 default 任务，所以我们直接使用 `gulp` 命令便可以执行 gulpfile.js 中的 default 任务
```
$ npm run dev
```

<br>

### 复制文件
使用 src 方法读取文件，然后使用 dest 方法输出文件。
```javascript
var gulp=require('gulp');

gulp.task('copy-index',function(){
  gulp.src('index.html').pipe(gulp.dest('dest'));
});
```

<br>

### 复制多个文件
- 可以使用匹配符来处理多个文件
- `images/**/*`表示images下的所有文件(包括所有子目录)
- `images/*.{png,jpg}`表示images下面的所有png和jpg文件
- 也可以使用数组，例如`['xml/*.xml','json/*.json']`
- 设置排除的文件，可以使用`!`。例如`!package.json`
```javascript
var gulp=require('gulp');

gulp.task('copy-images',function(){
  gulp.src('images/*.jpg').pipe(gulp.dest('dest/images'));
});
```

<br>

### 插件使用
例如 sass 编译工具

首先安装插件 gulp-sass
```
$ npm install gulp-sass --save-dev
```
然后在 pipe 方法中调用插件

```javascript
var gulp=require('gulp');
var sass=require('gulp-sass');
gulp.task('sass',function(){
  gulp.src('stylesheets/**/*.scss')
    .pipe(sass())
    .pipe(gulp.dest('dest/css'))
});
```

<br>
<br>

## 常用插件

- gulp-sass —— 编译 Sass 插件
- gulp-less —— 编译Less插件
- gulp-connect —— 本地服务器插件
- gulp-concat —— 合并文件插件
- gulp-uglify —— 压缩 JS 插件
- gulp-rename —— 文件重命名插件
- gulp-clean-css —— 压缩 css 插件
- gulp-imagemin —— 压缩图片插件
