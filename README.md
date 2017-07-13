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
		1. 参数:在指令后以冒号指明
		1).v-bind:href指令被用来响应地更新html属性href
		2).v-on:click用于监听DOM事件click
		2. 修饰符:以半角句号.指明的特殊后缀，用于指出一个指定应该以特殊方式绑定
		1).form->v-on:submit.prevent='onSubmit'->.prevent修饰符告诉v-on指令对于触发的事件调用event.preventDefault():
	3. 用户输入:
		1).在input输入框中我们可以使用v-model指令来实现双向数据绑定
		2).按钮事件可以使用v-on监听事件，并对用户的输入进行响应
	4. 过滤器:
		允许自定义过滤器，被用作一些常见的文本格式化。用‘管道符’指示，过滤器函数接受表达式的值作为第一个参数。
		1). 在两个大括号中
			{{message|capitalize}}
		2). 在v-bind指令中
			<div v-bind:id="rawId | formatId"></div>
		3). 过滤器可以串联
			{{ message | filterA | filterB }}
		4). 过滤器是JavaScript函数，因此可以接受参数
			{{ message | filterA('arg1', arg2) }}->message是第一个参数，字符串‘arg1'将传给过滤器作为第二个参数，arg2表达式的值将被求值然后传给过滤器作为第三个参数
	5. 缩写
		1. v-bind 缩写
			1. v-bind:href='url'（完整）->:href='url'（缩写）
		2. v-on 缩写
			1. v-on:click='dosomething'(完整)->@click='dosomething'(缩写)
	6. Vue 实例 2017/7/12 22:05:36 
		1. 构造器
			1. `var vm = new Vue({//选项})`
		2. 属性与方法
			1. 每个Vue实例都会代理其data对象里所有的属性
			2. 除了data属性,Vue实例暴露了一些有用的实例属性与方法，这些属性与方法都有前缀$以便与代理的data属性区分

## Vue.js--条件与循环

	1. 条件判读
		1. v-if->条件判断使用if指令
		2. v-else->用于给v-if添加一个else块
		3. v-else-if->用作if的else-if块，可以链式的多次使用----->后面这两种必须放在v-if或者v-else之后
		4. v-show->使用v-show指令来根据条件展示元素->不支持<template>语法
	2. 循环语句
		1. v-for 以item in items形式使用->items是源数据数组并且item是数组元素迭代的别名
			1. v-for可以绑定数据到数组来渲染一个列表
			2. v-for可以通过一个对象的属性来迭代数据
				1. `v-for='value in object'`	
				2. 可以提供第二个的参数为键名->
				`v-for='(value,key) in object'`
				3. 第三个参数为索引
				`v-for='(value,key,inidex) in objec'`
			3. v-for 迭代整数
				1. v-for也可以循环整数->`v-for='n in 10'`

## Vue.js--计算属性

### 计算属性关键词：computed

	1. methods vs computed
		效果上是一样的，
		但是computed基于他的依赖缓存，只有相关依赖改变时才会重新取值，
		methods在重新渲染的时候，函数总会重新调用执行
	2. computed setter
		computed属性默认只有getter,不过在需要时你可以提供一个setter

## Vue.js--样式绑定
	
	1. class属性绑定-> v-bind:class
		1. v-bind:class设置了一个对象,从而动态的切换class
		2. 绑定返回对象的计算属性
	2. style绑定-> v-bind:style
		1. v-bind:style直接设置样式
		2. 或者绑定一个样式对象，让模板更清晰
		3. 可以使用数组将对个样式对象应用到一个元素上
		4. 需要使用特定前缀的css属性时,会自动侦测并添加相应的前缀

## Vue.js--事件处理器
	
	1. v-on事件监听->
	2. 事件修饰符->处理DOM事件细节，如event.preventDefault() 或 event.stopPropagation()。通过由点(.)表示的指令后缀来调用修饰符
		1. v-on：click.stop='doThis'->阻止单击事件冒泡
		2. v-on：submit.prevent='onSubmit'->提交时间不再重载页面
		3. v-on:click.stop.prevent='doThis'->修饰符可以串联
		4. v-on:submit.prevent->只有修饰符
		5. v-on:click.capture='doThis'->添加事件侦听器时使用事件捕获模式
		6. v-on:click.self='doThis'->只当事件在该元素本身（而不是子元素）触发时触发回调
		7. v-on:click.once='doThis'->click事件至少触发一次
	3. 按键修饰符->为v-on在监听键盘事件时添加按键修饰符v-on:keyup.enter
		1. 基础
			1. v-on:keyup.13='submit'
		2. 为常用按键提供了别名
			1. v-on:keyup.enter='submit'->同上
			2. @keyup.enter='submit'->同上的缩写
		3. 全部按键别名
			1. .enter
			2. .tab
			3. .delete(捕获'删除'和'退格'键)
			4. .esc
			5. .space
			6. .up
			7. .down
			8. .left
			9. .right
			10. .ctrl
			11. .alt
			12. .shift
			13. .meta
		4. 实例
			1. @keyup.alt.67
			2. @click.ctrl

## Vue.js--表单
	
	1. 用v-model指令在表单控件元素上创建双向数据绑定->会根据控件类型自动选取正确的方法来更新元素
	2. input和textarea
	3. 复选框
		1. 复选框如果是一个为逻辑值，如果是多个则绑定到同一个数组
	4. 单选框
	5. select列表
	6. 修饰符
		1. lazy->在默认情况下， v-model 在 input 事件中同步输入框的值与数据，但你可以添加一个修饰符 lazy ，从而转变为在 change 事件中同步
			1. v-model.lazy='msg'
		2. number->自动将用户的输入值转为 Number 类型（如果原值的转换结果为 NaN 则返回原值）
			1. v-model.number='age' type='number'
		3. .trim->自动过滤用户输入的首位空格
			1. v-model.trim

## Vue.js--组件

	1. 注册一个全局组件->Vue.component(tagName,options)
		1. tagName为组件名，options为配置选项
		2. 使用-><tagName><tagName>
	2. 全局组件
	3. 局部组件->这个组件只能在这个实例中使用-> prop 是单向绑定的：当父组件的属性变化时，将传导给子组件，但是不会反过来
		1. Prop->是父组件用来传递数据的一个自定义属性
			1）. 父组件的数据需要通过 props 把数据传给子组件，子组件需要显式地用 props 选项声明 "prop"：	
		2. 动态 Prop
			1）.  类似于用 v-bind 绑定 HTML 特性到一个表达式，也可以用 v-bind 动态绑定 props 的值到父组件的数据中。每当父组件的数据变化时，该变化也会传导给子组件
		3. Prop 验证->props 指定验证要求。prop 是一个对象而不是字符串数组时，它包含验证要求
	4. 自定义事件
		1. 父组件是使用 props 传递数据给子组件，但如果子组件要把数据传递回去，就需要使用自定义事件！
			1. 使用 v-on 绑定自定义事件
				1. $on(eventName) 监听事件
				2. $emit(eventName) 触发事件
			2. 父组件可以在使用子组件的地方直接用 v-on 来监听子组件触发的事件。
			3. 你想在某个组件的根元素上监听一个原生事件。可以使用 .native 修饰 v-on 。 
			
## Vue.js--自定义指令
	
	1. `Vue.directive('focus', {// 当绑定元素插入到 DOM 中。inserted: function (el) {// 聚焦元素el.focus()}})`；
	2. 可以directives 选项来注册局部指令，这样指令只能在这个实例中使用
		 `new Vue({el:'#app',directives:{//注册一个局部的自定义指令v-focus focus:{}})`
	3. 钩子
		1. 钩子函数->指令定义函数提供了几个钩子函数（可选）
			1. bind:只调用一次，指令第一次绑定到元素时调用，用这个钩子函数可以定义一个在绑定时执行一次的初始化动作
			2. inserted：被绑定元素插入父节点时调用（父节点存在即可调用，不必存在于document中）
			3. update：被绑定元素所在的模板更新时调用，而不论绑定值是否变化。通过比较更新前后的绑定值，可以忽略不必要的模板更新
			4. componentUpdated:被绑定元素所在模板完成一次更新周期时调用
			5. unbind:只调用一次，指令与元素解绑时调用
		2. 钩子函数参数
			1. el:指令所绑定的元素，可以用来直接操作DOM
			2. binding:	一个对象，包含以下属性
				1. name:指令名，不包括v-前缀
				2. value：指令的绑定值
				3. oldValue：指令绑定的前一个值->仅在update和componentUpdated钩子总可用，无论值是否改变都可用
				4. expression：绑定值的字符串形式
				5. arg:传给指令的参数
				6. modifiers：一个包含修饰符的对象
			3. vnode:vue编译生成的虚拟节点
			4. oldVnode:上一个虚拟节点->仅在update和componentUpdated钩子中可用
			
## Vue.js--路由->需要载入vue-router库
	
	1. Vue.js + vue-router 可以很简单的实现单页应用。
		1. 引入vue&vue-router
		2. 然后配置组件和路由映射
		3. 告诉vue-router在哪里渲染
	