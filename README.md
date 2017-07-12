# Vue

  on the way!

## Vue.js--命令行操作
	
	$ npm install -g vue-cli -> 全局安装vue-cli
	$ vue init webpack my-project ->创建一个基于webpack模板的新项目
	$ cd my-project -> 调到当前文件
	$ npm install
	$ npm run dev

## Vue.js--目录结构 -> 2017/7/12 13:23:01 
	
	build 最终发布的代码存放位置
	config 配置目录，包括端口号等。初学可以默认
	node_modules npm加载的项目依赖模块
	src 开发目录
		assets: 放置一些文件,如logo等
		compontents: 目录里面放了一个组件文件，可以不用
		App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用compontents目录
		main.js: 项目的核心文件
	static: 静态资源目录,如图片、字体等
	test: 初始测试目录，可删除
	.****文件: 这些是一些配置文件，包括语法配置，git配置等。
	index.html 首页入口文件,你可以添加一些meta信息或同统计代码什么的
	package.json项目配置文件
	README.md 项目的说明文档，markdown格式

## Vue.js--模板语法
