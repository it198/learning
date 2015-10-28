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

	```