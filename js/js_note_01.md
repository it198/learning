## JS 学习笔记 01

### 12条专业的JavaScript规则

*  所有的 JS 都应该放在 `.js` 文件中 

	 独立js文件，有利于可读性、节省带宽、可被缓存；行内js每次加载都会重新下载。

* JS 应该是静态的

	动态引入JSON是例外，把 JSON 看作是数据，而不是代码。

* JS 应该被压缩

* JS 应该位于页面底部

	位于 `<head>` 中的脚本必须在页面显示前加载，因此把 `<script>` 放在底部的 前面可以先显示页面，而不用等 JS 文件下载完毕。这有助于提升感知性能。
	
* JS 应该实时的 Linted

	建议使用工具 [eslint](http://eslint.org/)
	
* JS应该有自动化测试

	[seleniumhq](http://www.seleniumhq.org/)
	
	[jasmine](http://jasmine.github.io/)
	
	[mochaj](https://mochajs.org/)
	
	[chaijs](http://chaijs.com/)
	
* JS 需要封装

	AMD 、 RequireJs 
	
	CommonJS
	
	ES6 modules
	
* JS 依赖应当明确

* Transpile to JS

	[babeljs](https://babeljs.io/)
	
	[TypeScript](http://www.typescriptlang.org/)
	
* JS应该自动构建

	Gulp / Grunt / Webpack / npm 
	
* 使用框架或者库

	[backbonejs](http://backbonejs.org/)
	
	[knockoutjs](http://knockoutjs.com/)
	
	[jquery](http://jquery.com/)
	
* JS Should Separate Concerns

	编写JavaScript的时候应该像服务器端开发者那样思考问题。把你的业务逻辑和数据访问分离出来。



	