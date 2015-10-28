学习资料 ： [深入理解JavaScript系列](http://www.kancloud.cn/kancloud/deep-understand-javascript/43686)

## JS代码的基本要求

### 最小全局变量(Minimizing Globals)

* JavaScript通过函数管理作用域。在函数内部声明的变量只在这个函数内部，函数外面不可用。另一方面，全局变量就是在任何函数外面声明的或是未声明直接简单使用的。

	```javascript

	myglobal = "hello"; // 不推荐写法
	
	console.log(myglobal); // "hello"

	console.log(window.myglobal); // "hello"

	console.log(window["myglobal"]); // "hello"

	console.log(this.myglobal); // "hello"
	
	console.log(this === window) //true

	```

### 全局变量的问题

* 共享全局变量，引起命名冲突。

* web页面往往包含非改页面开发者所写的代码 ：

	* 第三方的JavaScript库
	
	* 广告方的脚本代码
	
	* 第三方用户跟踪和分析脚本代码
	
	* 不同类型的小组件，标志和按钮
	
* 减少全局变量的策略

	* 命名空间模式
	
	* 函数立即自动执行 
	
	* 始终使用var声明变量
	
* 容易产生全局变量的例子

	```javascript
	
	function sum(x, y) {
	
   		//不推荐写法：隐式全局变量
   		result = x + y;
   		return result;
		
	}
	
	```
	