## Q：面向对象的语言特性？

### A：封装性、继承性、多态性。


## Q：在.NET中所有类的基类是？

### A：Object。


## Q：在C#中，&和&&的区别？

### A：&是按位与运算符(或取地址运算符)，&&是条件与运算符(也叫逻辑与运算符)。


## Q：委托声明的关键字是？

### A：delegate。


## Q：在.NET中所有可序列化的类都被标记为？

### A：Serializable。


## Q：一个类不想被继承应该？

### A：标记为sealed。


## Q：简单描述CLR?

### A：因为有了CLR的GC机制。正常情况下，.net会自动的帮忙释放内存,如果非托管代码，则需要手动释放，比如dataread、WebRequest。


## Q：如何对数组的元素进行倒序排列？

### A：xx.Sort()后xx.Reverse()。


## Q：HTTP定义的基本的与服务器交互的方法有？

### A：4种，分别是：GET获取、POST新建（也可以更新）、PUT更新、DELETE删除。


## Q：单点登录常用的实现方法有？

### A：
1. 存放用户凭证在Cookie中，但是依赖Cookie不太安全而且无法跨域
2. 使用jsonp，和cookie差不多，虽然能解决跨域但加密算法泄露还是不安全
3. token，现在比较常见的方式，通过反复重定向来验证，因为所有信息都存在服务端，所以即使知道了加密算法也无法登录，比较安全。但是项目调用比较复杂。


## Q：什么是继承？什么是重载？

### A：继承指子类可以拥有父类允许访问的属性、方法等。重载是一个函数通过参数类型或者数量区分不同的实现。


## Q：什么是接口类？

### A：定义了一组行为的集合，其中的方法不能有具体实现
。


## Q：什么是虚函数？什么是抽象函数?

### A：虚函数是子类可以被override的（也可以不）函数，在父类中必须实现。抽象函数必须存在于抽象类中，不允许有具体实现，它的子类必须实现该方法（有点像接口中的方法）


## Q：在ASP.NET页面之间传递值除了Session、Cookie、Application，还有什么其他方法？

### A：QueryString,POST,ViewData(基于字典),ViewBag(基于Dynamic)


## Q：ADO.net中常用的对象有哪些，其作用分别是什么？

### A：SqlConnection连接数据库，SqlCommand执行sql语句，SQLDataAdapter查询数据后填充到DataSet，DataSet中包含DataTable存放数据。


## Q：什么是SQL注入，如何防止SQL注入攻击？

### A：代码没有过滤特殊字符时，在执行sql语句处填入';等之类的字符来截断sql语句后再输入要执行的sql语句（删表等）来对数据库进行攻击。可以使用SQLParameter(把所有参数当字符串而不是关键字来处理或)者ORM来避免。


## Q：使用递归输出斐波那契数列，并输出第X项。

### A：
```
int fb(int i)
{
	if(i<1) return 0;
	else if(i<=2) return i;
	else return fb(i-1)+fb(i-2);
}
```


## Q：将字符串www.abc.com逆序输出为”com.abc.www”。

### A：str.Split('.').Sort().Reverse()


## Q：原生js的ajax？

### A：em..........


## Q：在SQL环境下，写一个T-SQL函数，求从今天往后数的7000天，所在日期的当月有多少天？

### A：
```
declare @date_time datetime,@day_num int,@d int
 set @date_time=dateadd(d,7000,getdate())
 set @d=month(@date_time)
 if @d=12
 set @day_num=31
 else

 set @day_num=day(dateadd(d,-1,(cast(year(@date_time) as varchar(4))+'-'+cast((month(@date_time)+1) as varchar(2))+'-01')) )

 select @day_num as count,@d as month,@date_time
```
网上抄的


## Q：写一个存储过程，可以清空任意一个表的数据？

### A：
```
create proc deltb
@tname char(20) --入参
as
declare @cmd char(50)='truncate table '+@tname
exec(@cmd)


exec deltb '表名'
```


## Q：请列出UML中几种视图的名称，并解释其中两种视图的作用？

### A：em...............


## Q：请描述设计模式的含义，并写出你所了解的几中设计模式的名称？

### A：通过面向对象特性更好的解耦代码，用过单例和工厂。


## Q：如何部署一个ASP.NET项目？

### A：VS发布到文件夹，拷到服务器上，IIS指定目录并绑定IP（域名）。


## Q：写出验证中国移动手机号码的正则表达式？

### A：1\d{10}	(不知道中国移动的开头是啥)


## Q：如何在所有页面加载时输出内容？

### A：使用HTTPModule/中间件或者Filter。


## Q：什么是串行化？

### A：将数据使用BinaryFormat从Stream保存到二进制文件，这种文件大小都是2的平方。


## Q：用一个xml文件描述你自己？

### A：
```
<me>
	<name>姓名</name>
	<sex>男</sex>
	<age>24</age>
</me>
```


## Q：判断一个字符串中出现次数最多的字符，并统计这个次数？

### A：遍历字符串，创建字典，以char为key,value默认1，如果字典key中包含char则value+1。最后输出字典


## Q：什么是装箱和拆箱？

### A：值类型到object是装箱，object到值类型是拆箱


## Q：C#中委托是什么？事件是不是一种委托？

### A：委托是传递一个方法的引用，类似函数指针。事件是一种特殊的委托。


## Q：Override和重载的区别？

### A：override是重写方法的关键字，重载指一个方法的不同实现。


## Q：什么叫应用程序域？

### A：就是程序之间的边界，可以理解一个程序是一个应用程序域。


## Q：

### A：
