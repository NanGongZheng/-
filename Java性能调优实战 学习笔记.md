
1.String字符串
 string被final修饰不可继承，底层是char[]被final+private，则加上不可更改。

 ① String str=“abc”
 ② String str = new String(“abc”)
①JVM首先会检查该对象是否在字符串常量池中，如果在，就返回该对象引用，否则新的字符串将在常量池中被创建。这种方式可以减少同一个值的字符串对象的重复创建，节约内存。
②首先在编译类文件时，"abc"常量字符串将会放入到常量结构中，在类加载时，“abc"将会在常量池中创建；其次，在调用new时，JVM命令将会调用String的构造函数，同时引用常量池中的"abc” 字符串，在堆内存中创建一个String对象；最后，str将引用String对象。


平常一些字符串拼接的写法，本质是修改了地址指向，原本的对象没有变。


使用String.intern节省内存
在每次赋值的时候使用String的intern方法，如果常量池中有相同值，就会重复使用该对象，返回对象引用，这样一开始的对象就可以被回收掉。


String str1= "abc";
String str2= new String("abc");
String str3= str2.intern();
assertSame(str1==str2);
assertSame(str2==str3);
assertSame(str1==str3);

答案：false,false,true


2.正则表达式
慎用：Split()方法，匹配过程中会引起回溯（匹配失败会重回上一个进行匹配），占用大量CPU


![正则表达式](http://image.huawei.com/tiny-lts/v1/images/72d71cfdf55c520885ed1f3fd504151e_1782x800.png)


3.Stream

![stream](http://image.huawei.com/tiny-lts/v1/images/a300022e0c166d7e494ebf0d7a25ce3d_2036x1438.png)


