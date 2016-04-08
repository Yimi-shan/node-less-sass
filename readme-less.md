安装less  → → →

cnpm install glup -g

cnpm install gulp-less -g

cnpm install gulp-connect -g

---------------------------------------------------------

sublime 使用less → → →

新建一个文件夹为www，把网页等内容放进这里
新建gulpfile.js(与www同一路径下)

var gulp = require('gulp');//加载gulp工具
var less = require('gulp-less');//加载LESS插件
var sass = require('gulp-sass');//加载LESS插件
var connect = require('gulp-connect');//启动一个服务器

//使用connect启动一个www服务器
gulp.task('connect', function () {
  connect.server({
    root: 'www',
    port: 9999,
    livereload: true
  });
});

// Styles
gulp.task('less', function() {
    //编译less
    return gulp.src('./www/css/*.less')
    .pipe(less())
    //保存未压缩文件到我们指定的目录下面
    .pipe(gulp.dest('./www/css'))
    .pipe(connect.reload())
});

// Styles
gulp.task('sass', function() {
    //编译less
    return gulp.src('./www/css/*.scss')
    .pipe(sass())
    //保存未压缩文件到我们指定的目录下面
    .pipe(gulp.dest('./www/css'))
    .pipe(connect.reload())
});



gulp.task('html', function () {
  gulp.src('./www/*.html')
    .pipe(connect.reload());
});

//watch监听
gulp.task('watch', function () {
  gulp.watch(['./www/*.html','./www/css/*.less','./www/css/*.scss'], ['less','html','sass']);
});


gulp.task('default', ['connect', 'watch']);



-------配置环境------
node_path
C:\Users\a\AppData\Roaming\npm\node_modules

--------cmd------
cd C:\Users\a\Desktop\gulp-less（地址）
gulp

---------访问----
pc端 
localhost:9999
IP:9999
移动端
IP:9999


---------------------------------------------------------
