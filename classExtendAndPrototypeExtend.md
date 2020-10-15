### 关于类式继承和原型式继承

#### 类式继承
> 定义：通过用函数来声明类、用关键字new来创建实例

> 过程：
>>>	1. 首先要做的式创建构造函数。按惯例，其名称就是类名，首字母应大写
>>>	2. 在构造函数中，创建实例属性要使用关键字this。
>>>	3. 下一步是设置原型链。JavaScript没有extend关键字。但是在JavaScript中每一个对象都有一个名为prototype的属性，这个属性要么指向另一个对象，要么是null。在访问对象的某个成员时，
>>>>>	如果这个成员未见于当前对象，那么JavaScript会在prototype属性所指的对象中查找它。如果在那个对象中也没有找到，那么JavaScript会沿着原型链向上逐一访问每个原型对象，直接找到这个成员
>>>>>	（或已经查过原型链最顶端的Object.prototype对象）。这意味着为了让一个类继承另一个类，只需将子类的prototype设置为指向超类的一个实例即可。这与其他语言中的继承机制迥然不同，可能会非常令人费解，而且有违直觉。
>>>>>	为了让Author继承Person，必须手工将Author的prototype设置为Person的一个实例。最后一个步骤是将prototype的constructor属性重设为Author（因为把prototype属性设置为Person的实例时，其constructor属性被抹除了）。
>>>	4. 类的方法则被添加到其prototype对象，然后可以访问所有的实例属性，也可以调用所有的实例方法。
> 显著特点：每一次实例化对象时，子类都将执行一次父类的构造函数。
```
function extend(subClass, supClass){
	var F = function() {}
	F.prototype = supClass.prototype;
	subClass.prototype = new F();
	subClass.prototype.constructor = subClass;

	subClass.supclass = superClass.prototype;
	if (superClass.prototype.constructor ==  Object.prototype.constructor) {
		superClass.prototype.constructor = superClass;
	}
}


// 在子类中需要调用 
function Author(name, books) {
	Author.superclass.constructor.call(this, name); // superclass可以用来弱化Author与Person之间的耦合，有了这个属性，就可以直接调用超类中的方法
	this.books = books;
}
extend(Author, Person);

Author.prototype.getBooks = function(){
	return this.books;
}
Author.prototype.getName = function(){
	var name = Author.superclass.getName.call(this);
	return name + ', Author of ' + this.getBooks().join(', ');
}
```

#### 原型式继承
```
function clone(object){
	function F() {}
	F.prototype = object;
	return new F;
}
```

#### 类式继承与原型式继承的区别与相似之处
1. 类式继承中：使用构造函数初始化对象的属性，通过调用符类的构造函数来继承这些属性。通过new 父类的 porotype 来继承方法
2. 原型式继承中： 去掉了构造函数，但需要将对象的属性和方法写一个{}里申明。准确的说，原型式继承就是类式继承中继承符类的prototype方法