##### 1.方法的反射

A a=newA\(\);

//1.获取方法对象getMethod\(方法名，参数列表\);

Method m =a.class.getMethod\("print",newClass{int.class,int.class}\);

Method m =a.class.getMethod\("print",int.class,int.class\);

//2.方法反射操作用m对象进行方法调用m.invoke\(对象，参数列表\);

//m.invoke\(a,Object\[\]{10,20}\);

m.invoke\(a,Object\[\]{10,20}\);



##### 2.Class.Method\(\)认识泛型的本质。

//编译之后集合的泛型是去泛型化的。java泛型是防止错误输入的只在编译期有效

//验证：通过方法的反射操作，绕过编译

//如下，往list加入20

ArrayList&lt;String&gt; list=new arrarList&lt;String&gt;\(\);

Object c=list.getClass\(\);

Methodm=c.getMethod\("add",Object.class\);

m.invoke\(list,20\);//绕过泛型











