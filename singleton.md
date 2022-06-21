### 单体模式
1. 概念：这种模式提供了一种将代码组织为一个逻辑单元的手段，这个逻辑单元中的代码可以通过单一的变量进行访问。
通过确保单体对象只存在一份实例，你就可以确信自己的所有代码使用的都是同样的全局资源。

2. 定义：
> 传统定义：单体是一个只能被实例化一次并且可以通过一个众所周知得访问点访问得类。
> 广义定义：单体式一个用来划分命名空间并将一批相关方法和属性在一起得对象。如果它可以被实例化，那么它只能被实例化一次

3. 用途：
- 用来划分命名空间，以减少网页中全局变量的数目。
- 还可以在一种名为分支(branching)的技术中用来封装浏览器之间的差异（借助分支结束，你在使用各种常用的工具函数时就不必再操心浏览器嗅探的事）
- 可以把代码组织得更为一直，从而使其更容易阅读和维护

```
/*
	对象字面量只是用来创建单体得方法之一。
	简单得单体模式实际上就是一个对象字面量，它把一批有一定关联得方法和属性组织在一起：
*/
var Singleton = {
	attribute1: true,
	attribute2: 10,
	method1: function(){},
	method2: function(arg){}
}
```

####划分命名空间
单体对象由两个部分组成：包含着方法和属性成员的对象自身，以及用于访问它的变量。
>>> 这个变量通常是全局性的，以便在网页上任何地方都能直接访问到它所指向的单体对象。
>>> 按定义单体不必是全局性的，但它们应该在各个地方都能被访问。因为单体对象的所有内部成员都被包装在这个对象中，所以它们不是全局性的。由于这些成员只能通过
这个单体对象变量进行访问，因此在某种意义上，可以说他们被单体对象圈在了一个命名空间中

- 私有成员、私有方法和公共属性、公共方法
```
GiantCorp.DataParser = (function(){
	// Private attributes
	var whitespaceRegex = /\s+/;

	// private mthods
	function stripWhitespace(str){
		return str.replace(whitespceRegex, '');
	}
	function stringSplit( str, delimiter){
		return str.split(delimiter);
	}

	//Everything returned in the object literal is public, but can access the members in the closure created above.
	return {
		//public method.
		StringToArray: function(str, delimiter, stripWs) {
			if (stripWs) {
				str = stripWhitespace(str);
			}
			var outputArray = stringSplit (str, delimiter);
			return outputArray;
		}
	}
})();
```