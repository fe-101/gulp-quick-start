gulp 快速入门 ![](https://img.shields.io/github/license/mashape/apistatus.svg) 
=== 

> 基于流的自动化构建工具

<!-- TOC -->

- [API](#api)
- [gulp 的使用](#gulp-的使用)
- [常用插件](#常用插件)

<!-- /TOC -->

<br>
<br>

## API
gulp 只有四个 API , task 用来创建任务，src 用来读取文件，watch 用来监视文件，dest 用来输出文件。还有用到 node 中的 pipe 方法，pipe 方法返回目标流的引用，这样就可以对流进行链式地管道操作。
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
