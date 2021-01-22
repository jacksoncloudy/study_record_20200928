# JavaScript记录忽略或者不常用的小知识

## script加载
1. 使用 defer 属性可以让脚本在文档完全呈现之后再执行。延迟脚本总是按照指定它们的顺序执行
2. 使用 async 属性可以表示当前脚本不必等待其他脚本，也不必阻塞文档呈现。不能保证异步脚本按照它们在页面中出现的顺序执行
3. 使用 <noscript>元素可以指定在不支持脚本的浏览器中显示的替代内容。但在启动了脚本的情况下，浏览器不会显示 <noscript> 中的任何内容

## 窗口关系及框架
如果页面中包含框架，则每个框架都拥有自己的window对象，并且保存再frames集合中。在frames集合中，可以通过数值索引（从0开始，从左至右，从上到下）或者框架名称来
访问相应的window对象。每个对象都有一个name属性，其中包含框架的名称。
- window.frames[0]    window.frames["topFrame"]
```
<frameset rows = "160, *">
	<frame src="frame.htm" name="topFrame">
	<frameset cols="50%,50%”>
		<frame src="frame.htm" name="leftFrame">
		<frame src="frame.htm" name="rightFrame">
	</frameset>
</frameset>
```
最好使用top而非window来引用这些框架：top.frames[0]
1. top对象始终指向最高（最外）层的框架，也就是浏览器窗口。使用它可以确保在一个框架中正确访问另一个框架。因为对于在一个框架中编写的任何代码来说，其中的window对象
指向的都是那个框架的特定实例，而非最高层的框架。
2. 与top相对的另一个window对象是parent。顾名思义，parent对象始终指向当前框架的直接上层框架。在某些情况下，parent有可能等于top；但在没有框架的情况下，parent一定
等于top（此时它们都等于window）


## location对象
1. 立即打开新URL并在浏览器的历史记录中生成一条记录（注意：每次修改 location 的属性 - hash除外，页面都以新URL重新加载。
```
	location.assign('http://www.wrox.com');
	window.location = 'http://www.wrox.com';
	location.href = 'http://www.wrox.com';
```
2. 用 replace ，会导致浏览器位置改变，但不会在历史记录中生成新记录。（用户不能回到前一个页面）。
```
	location.replace('http://www.wrox.com');
```
