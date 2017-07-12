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
	
	1. 插值：
		1).文本--{{}}
		数据绑定最常见的形式就是使用{{}}（双大括号）的文本插值
		2).Html--v-html
		使用v-html指令用于输出html代码
		3).属性--v-bind
		html属性中的值应使用v-bind指令
		4).JavaScript表达式支持--三木运算等
	2. 指令:指令是带有v-前缀的特殊属性
		指令用于在表达式的值改变时，将某些行为应用到DOM上
	3. 参数:在指令后以冒号指明
		1).v-bind:href指令被用来响应地更新html属性href
		2).v-on:click用于监听DOM事件click
	4. 修饰符:以半角句号.指明的特殊后缀，用于指出一个指定应该以特殊方式绑定
		1).form->v-on:submit.prevent='onSubmit'->.prevent修饰符告诉v-on指令对于触发的事件调用event.preventDefault():
	5. 用户输入:在input输入框中我们可以使用v-model指令来实现双向数据绑定
		1).过滤器:
		允许自定义过滤器，被用作一些常见的文本格式化。用‘管道符’指示，过滤器函数接受表达式的值作为第一个参数。
			1). 在两个大括号中
			{{message|capitalize}}
			2). 在v-bind指令中
			<div v-bind:id="rawId | formatId"></div>
			3). 过滤器可以串联
			{{ message | filterA | filterB }}
			4). 过滤器是JavaScript函数，因此可以接受参数
			{{ message | filterA('arg1', arg2) }}->message是第一个参数，字符串‘arg1'将传给过滤器作为第二个参数，arg2表达式的值将被求值然后传给过滤器作为第三个参数
	6. 缩写
		1. v-bind 缩写
			1. v-bind:href='url'（完整）->:href='url'（缩写）
		2. v-on 缩写
				
		
		
