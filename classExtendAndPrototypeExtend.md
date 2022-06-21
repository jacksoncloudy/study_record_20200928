### ������ʽ�̳к�ԭ��ʽ�̳�

#### ��ʽ�̳�
> ���壺ͨ���ú����������ࡢ�ùؼ���new������ʵ��

> ���̣�
>>>	1. ����Ҫ����ʽ�������캯�����������������ƾ�������������ĸӦ��д
>>>	2. �ڹ��캯���У�����ʵ������Ҫʹ�ùؼ���this��
>>>	3. ��һ��������ԭ������JavaScriptû��extend�ؼ��֡�������JavaScript��ÿһ��������һ����Ϊprototype�����ԣ��������Ҫôָ����һ������Ҫô��null���ڷ��ʶ����ĳ����Աʱ��
>>>>>	��������Աδ���ڵ�ǰ������ôJavaScript����prototype������ָ�Ķ����в�������������Ǹ�������Ҳû���ҵ�����ôJavaScript������ԭ����������һ����ÿ��ԭ�Ͷ���ֱ���ҵ������Ա
>>>>>	�����Ѿ����ԭ������˵�Object.prototype���󣩡�����ζ��Ϊ����һ����̳���һ���ֻ࣬�轫�����prototype����Ϊָ�����һ��ʵ�����ɡ��������������еļ̳л�����Ȼ��ͬ�����ܻ�ǳ����˷ѽ⣬������Υֱ����
>>>>>	Ϊ����Author�̳�Person�������ֹ���Author��prototype����ΪPerson��һ��ʵ�������һ�������ǽ�prototype��constructor��������ΪAuthor����Ϊ��prototype��������ΪPerson��ʵ��ʱ����constructor���Ա�Ĩ���ˣ���
>>>	4. ��ķ�������ӵ���prototype����Ȼ����Է������е�ʵ�����ԣ�Ҳ���Ե������е�ʵ��������
> �����ص㣺ÿһ��ʵ��������ʱ�����඼��ִ��һ�θ���Ĺ��캯����
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


// ����������Ҫ���� 
function Author(name, books) {
	Author.superclass.constructor.call(this, name); // superclass������������Author��Person֮�����ϣ�����������ԣ��Ϳ���ֱ�ӵ��ó����еķ���
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

#### ԭ��ʽ�̳�
```
function clone(object){
	function F() {}
	F.prototype = object;
	return new F;
}
```

#### ��ʽ�̳���ԭ��ʽ�̳е�����������֮��
1. ��ʽ�̳��У�ʹ�ù��캯����ʼ����������ԣ�ͨ�����÷���Ĺ��캯�����̳���Щ���ԡ�ͨ��new ����� porotype ���̳з���
2. ԭ��ʽ�̳��У� ȥ���˹��캯��������Ҫ����������Ժͷ���дһ��{}��������׼ȷ��˵��ԭ��ʽ�̳о�����ʽ�̳��м̳з����prototype����