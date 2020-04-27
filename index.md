#关于Vue项目移动端适配的一些总结
我们用到的是 flexible和 postcss-px2rem 两个插件
首先下载插件npm install lib-flexible postcss-px2rem --save
flexible会为页面根据屏幕自动添加<meta name='viewport' >标签，动态控制initial-scale，maximum-scale，minimum-scale等属性的值。
postcss-px2rem会将px转换为rem，rem单位用于适配不同宽度的屏幕，根据<html>标签的font-size值来计算出结果
在项目入口文件main.js 中引入lib-flexible
import 'lib-flexible'
注意事项（important）: 由于flexible会动态给页面header中添加<meta name='viewport' >标签，所以务必请把目录 public/index.html 中的这个标签删除！！！
在vue.config.js配置postcss-px2rem
module.exports = {
	css: {
		loaderOptions: {
			css: {},
			postcss: {
				plugins: [
					require('postcss-px2rem')({
						remUnit: 37.5
					})
				]
			}
		}
	}
}
重启我们的项目，在项目中使用PX作为单位就可以了。

#该文章根据(https://www.cnblogs.com/lml2017/p/9953429.html)书写完成，为了方便查看上传至本人github。