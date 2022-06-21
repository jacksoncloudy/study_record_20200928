### ����ģʽ
1. �������ģʽ�ṩ��һ�ֽ�������֯Ϊһ���߼���Ԫ���ֶΣ�����߼���Ԫ�еĴ������ͨ����һ�ı������з��ʡ�
ͨ��ȷ���������ֻ����һ��ʵ������Ϳ���ȷ���Լ������д���ʹ�õĶ���ͬ����ȫ����Դ��

2. ���壺
> ��ͳ���壺������һ��ֻ�ܱ�ʵ����һ�β��ҿ���ͨ��һ��������֪�÷��ʵ���ʵ��ࡣ
> ���嶨�壺����ʽһ���������������ռ䲢��һ����ط�����������һ��ö�����������Ա�ʵ��������ô��ֻ�ܱ�ʵ����һ��

3. ��;��
- �������������ռ䣬�Լ�����ҳ��ȫ�ֱ�������Ŀ��
- ��������һ����Ϊ��֧(branching)�ļ�����������װ�����֮��Ĳ��죨������֧����������ʹ�ø��ֳ��õĹ��ߺ���ʱ�Ͳ����ٲ����������̽���£�
- ���԰Ѵ�����֯�ø�Ϊһֱ���Ӷ�ʹ��������Ķ���ά��

```
/*
	����������ֻ��������������÷���֮һ��
	�򵥵õ���ģʽʵ���Ͼ���һ������������������һ����һ�������÷�����������֯��һ��
*/
var Singleton = {
	attribute1: true,
	attribute2: 10,
	method1: function(){},
	method2: function(arg){}
}
```

####���������ռ�
�������������������ɣ������ŷ��������Գ�Ա�Ķ��������Լ����ڷ������ı�����
>>> �������ͨ����ȫ���Եģ��Ա�����ҳ���κεط�����ֱ�ӷ��ʵ�����ָ��ĵ������
>>> �����嵥�岻����ȫ���Եģ�������Ӧ���ڸ����ط����ܱ����ʡ���Ϊ�������������ڲ���Ա������װ����������У��������ǲ���ȫ���Եġ�������Щ��Աֻ��ͨ��
����������������з��ʣ������ĳ�������ϣ�����˵���Ǳ��������Ȧ����һ�������ռ���

- ˽�г�Ա��˽�з����͹������ԡ���������
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