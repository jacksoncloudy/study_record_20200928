# JavaScript��¼���Ի��߲����õ�С֪ʶ

## script����
1. ʹ�� defer ���Կ����ýű����ĵ���ȫ����֮����ִ�С��ӳٽű����ǰ���ָ�����ǵ�˳��ִ��
2. ʹ�� async ���Կ��Ա�ʾ��ǰ�ű����صȴ������ű���Ҳ���������ĵ����֡����ܱ�֤�첽�ű�����������ҳ���г��ֵ�˳��ִ��
3. ʹ�� <noscript>Ԫ�ؿ���ָ���ڲ�֧�ֽű������������ʾ��������ݡ����������˽ű�������£������������ʾ <noscript> �е��κ�����

## ���ڹ�ϵ�����
���ҳ���а�����ܣ���ÿ����ܶ�ӵ���Լ���window���󣬲��ұ�����frames�����С���frames�����У�����ͨ����ֵ��������0��ʼ���������ң����ϵ��£����߿��������
������Ӧ��window����ÿ��������һ��name���ԣ����а�����ܵ����ơ�
- window.frames[0]    window.frames["topFrame"]
```
<frameset rows = "160, *">
	<frame src="frame.htm" name="topFrame">
	<frameset cols="50%,50%��>
		<frame src="frame.htm" name="leftFrame">
		<frame src="frame.htm" name="rightFrame">
	</frameset>
</frameset>
```
���ʹ��top����window��������Щ��ܣ�top.frames[0]
1. top����ʼ��ָ����ߣ����⣩��Ŀ�ܣ�Ҳ������������ڡ�ʹ��������ȷ����һ���������ȷ������һ����ܡ���Ϊ������һ������б�д���κδ�����˵�����е�window����
ָ��Ķ����Ǹ���ܵ��ض�ʵ����������߲�Ŀ�ܡ�
2. ��top��Ե���һ��window������parent������˼�壬parent����ʼ��ָ��ǰ��ܵ�ֱ���ϲ��ܡ���ĳЩ����£�parent�п��ܵ���top������û�п�ܵ�����£�parentһ��
����top����ʱ���Ƕ�����window��


## location����
1. ��������URL�������������ʷ��¼������һ����¼��ע�⣺ÿ���޸� location ������ - hash���⣬ҳ�涼����URL���¼��ء�
```
	location.assign('http://www.wrox.com');
	window.location = 'http://www.wrox.com';
	location.href = 'http://www.wrox.com';
```
2. �� replace ���ᵼ�������λ�øı䣬����������ʷ��¼�������¼�¼�����û����ܻص�ǰһ��ҳ�棩��
```
	location.replace('http://www.wrox.com');
```
