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


## Q：什么是不受管制的代码？

### A：unsafe关键字里写的非托管代码。不经过CLR运行。可以写指针等骚操作。


## Q：string str = null和string str = “”的区别？
### A：null表示不存在于内存中没有地址，“”表示存在于内存中的“”这个对象


## Q：描述class和struct异同？
### A：class是引用类型放在堆上的，struct是值类型放在栈上的。


## Q：能用foreach遍历访问的对象需要实现_____接口或声明_____方法的类型。
### A：IEnumerable接口、GetEnumerator()方法


## Q：GC是什么？为什么需要GC？
### A：GC（Garbage Collector）是垃圾收集器。.net中垃圾收集器会自动对内存垃圾进行回收管理。


## Q：接口可否继承接口？抽象类可否实现接口？抽象类可否继承实体类？
### A：接口可以继承接口。抽象类可以实现接口。抽象类可以继承实体类*（但是实体类必须有可访问的构造函数，所有类都无法继承只有private构造函数的实体类）*。


## Q：try里有一个return语句，那么finally中的代码会不会执行，在return前还是return后？
### A：会，在return前执行。看反编译会发现finally的代码放在了函数出口之前。


## Q：两个对象值相同x.equals(y)==true，但可能有不同的hash code，这个说法对吗？
### A：==比较地址，equals比较值*（等比地址Equals值）*。两个对象值相同则表示拥有相同的HashCode。


## Q：进程和线程的区别？
### A：进程是系统进行资源分配和调度的单位；线程是CPU分配和调度的单位。一个进程可以有多个线程，这些线程共享这个进程的资源。*（进程是系统层面，线程是CPU层面。线程∈进程）*


## Q：堆和栈的区别？
### A：栈上放的是由编译器自动分配释放的资源。堆上放的是代码中自己分配释放的资源，比如new对象时分配的内存空间。


## Q：请指出GAC的含义？
### A：（Global Assembly Cache）全局程序集缓存。应该是指常用到的dll（比如System.Data,System.Collections）会缓存在windows一个指定的文件夹下，别的程序再使用的话就直接调用，不用重新加载了。em....没折腾过。


## Q：DataReader和DataSet有什么区别？
### A：DataReader是读取数据库的（游标类似）。DataSet是用来存放数据的。


## Q：软件开发一般有几个阶段？每个阶段的作用？
### A：需求分析，详细设计（架构设计），代码编写，测试，部署


## Q：什么是强类型？什么是弱类型？哪种更好？为什么？
### A：需要在编译时定义变量类型的是强类型，比如User   user= new User();不需要指定类型的为弱类型如js  var user={};好坏看业务需求，各有千秋。


## Q：什么是反射？
### A：在程序运行时动态获取程序集信息：接口、类、方法、属性等。


## Q：编程求从0-1000一共输出了多少个0？需要JS和C#？
### A：em.........抖个机灵，js参照这个。
```
var str = "";
for (int i = 0; i < 1000; i++)
{
    str += i.ToString();
}
Console.WriteLine(str.Split('0').Length-1);
```


## Q：表如下：用一条SQL语句显示如图的结果？
表1：

| id | department |
| :------| :------ |
| 1 | 设计 |
| 2 | 市场 |
| 3 | 售后 |

表2：

| id | dptID | name |
| :------| :------ | :------ |
| 1 | 1 | 张三 |
| 2 | 1 | 李四 |
| 3 | 2 | 王五 |
| 4 | 3 | 彭六 |
| 5 | 4 | 陈七 |
| 6 | 5 | 陈七 |

结果：

| id | dptID | department | name |
| :------| :------ | :------ | :------ |
| 1 | 1 | 设计 | 张三 |
| 2 | 1 | 设计 | 李四 |
| 3 | 2 | 市场 | 王五 |
| 4 | 3 | 售后 | 彭六 |
| 5 | 4 | 黑人 | 陈七 |


### A：**isnull(列名，'指定值')可以使用coalesce(列名，'指定值')替换，结果一样**
```
select min(u.id) as id, 
	   min(u.dptID) as dptID, 
	   isnull(d.department,'黑人') as department,
	   u.name 
from users as u left join dpt as d on  u.dptID=d.id
group by name,department 
order by id
```


## Q：.NET中lock关键字根据什么来产生边界（线程同步）？
### A：静态变量。（static  object o=new Object();）


## Q：在.NET中引入ref和out关键字的根本原因是什么?
### A：方法中操作的对象的地址和传入的参数地址不一致。ref修饰的变量在方法中改变值时候，实际参数也会改变。


## Q：.NET中的new关键字和override关键字的异同？
### A：要重写的方法都需要virtual关键字，但是override是重写了父类的方法，调用的话是子类重写后的方法；new是重新写了一个同名的方法，隐藏了父类的方法。**如果把子类强制转换为父类的话new调用还是父类的方法，而override则调用子类重写的方法。**


## Q：.NET MVC框架是通过什么来解析HTTP请求的。
### A：请求的method。。。。（一时半会没理解）


## Q：MD5实质是？
### A：一种哈希（hash）散列**算法**。将字符串转换为字节数组后计算数组的hash值。


## Q：分布式分类？
### A：
1. 应用分布式：程序部署在多台机器上
2. 缓存分布式：缓存部署在多台机器上
3. 数据库分布式：数据库部署在多台机器上
*我当时就这么瞎几把回答的*


## Q：后台接口如何鉴权？比如开发了一个后台管理系统，如何防止别人拿到你请求的接口恶意攻击？
### A：OAuth使用accessToken访问。或者使用JWT


## Q：纯webapi项目，前端请求的用户信息存储在哪里？
### A：web的话localStorage。不同端有不同的存储方式。


## Q：vue生命周期？
### A：四种两类。（vue对象）创建前/后，挂载前/后（vue挂载到页面），更新前/后，销毁前/后。


## Q：多线程的线程同步如何实现？
### A：
1. 使用Monitor/lock关键字创建临界区
2. 读写锁
	```
	static private ReaderWriterLock _rwlock = new ReaderWriterLock(); 
	// 请求读锁，如果10ms超时退出 
    _rwlock.AcquireReaderLock(10); 
    //...读取数据
    _rwlock.ReleaseReaderLock(); //释放读锁
    // 请求写锁，如果100ms超时退出 
    _rwlock.AcquireWriterLock(100); 
    //...写入数据
    _rwlock.ReleaseWriterLock(); //释放写锁
	```
3. 系统级别的：信号量（Semaphore），互斥（Mutex），事件(AutoResetEvent/ManualResetEvent) 。线程池
	1. 信号量（Semaphore）：
	   ```
	    //当前允许同时访问线程数2; 最大允许数量=3 
        static Semaphore s = new Semaphore(2, 3); 
        static void Main(string[] args)
        {
            for (int i = 0; i < 10; i++)
                new Thread(Go).Start();
            Console.ReadLine();
        }
        static void Go()
        {
            while (true)
            {
                //WaitOne()和Release()必须成对出现，否则会一直等待/释放出错
                s.WaitOne();
                Thread.Sleep(1000); //因为当前数量为2，所以每sleep后输出2行 
                Console.WriteLine(Thread.CurrentThread.ManagedThreadId);
                s.Release();
            }
        }
	   ```
	   2. 互斥（Mutex）:
	   ```
   	 	var _mtx = new Mutex();
        var _resource = new List<string>();
        // 设置超时时限并在wait前退出非默认托管上下文 
        if (_mtx.WaitOne(1000, true))
        {
            _resource.Add("123");
            _mtx.ReleaseMutex();
            //WaitOne和ReleaseMutex必须成对出现，
            //否则会导致进程死锁的发生，会抛出AbandonedMutexException异常。
        }
	   ```
	   3. 事件(AutoResetEvent/ManualResetEvent)
	   ```
	    //处理线程等待的对象
        //false是手动set唤醒，如果传true则会在线程执行时自动set
        static EventWaitHandle wh = new AutoResetEvent(false);
        static void Main()
        {
            new Thread(Waiter).Start();//1
            new Thread(Waiter).Start();//2
            new Thread(Waiter).Start();//3
            Thread.Sleep(3000); //做任何耗时操作
            //唤醒，继续执行刚才线程输出
            wh.Set();  
            //因为是AutoResetEvent，所以自动重置等待，到1执行的时候，抛弃后续23线程的输出
            Console.ReadKey();
        }
        static void Waiter()
        {
            Console.WriteLine("Waiting...");
            wh.WaitOne(); //等待唤醒之后继续往下执行
            Console.WriteLine("Notified");
        }
	   ```
	   ManualResetEvent与AutoResetEvent区别是M需要手动调用M.Reset()重置等待
	   4. 线程池（em.....暂时看不懂搜出来的东西）

## Q：redis大数据并发（例如秒杀活动，放到redis时并发怎么处理）？
### A：为redis加锁，别的进程判断如果锁存在则等待，直到锁被释放（通过时间戳等机制优化解决死锁）


## Q：Memochached（与redis区别）、UML用过吗？
### A：用过Memochached，与redis的区别是redis有机制不是所有数据都放在内存中，会放磁盘一部分（重启不丢失）。redis支持更多数据类型（list,set,zset,hash）,redis是单线程。Memcached单个value最大只支持1MB，Redis最大支持512MB。UML没用过。


## Q：数据库锁了解过吗？
### A：共享（S)锁、排它（X)锁、更新（U)锁。


## Q：EF避免脏读？
### A：我们只需要在实体中增加一个byte[]类型的字段，并为其加上[Timestamp]特性:
```
public class Entity
{
	public string Name {get; set;}
	[Timestamp]
	public byte[] v {get; set;}	
}
```
这样在更新或删除操作生成的Sql中，Where语句将包含 and v = @2 条件，如果有其它用户更改过此行，那么行版本将不一致，因此更新或删除sql会无法找到要更新的行，此时EF将认定该操作出现了并发冲突。
如果是控制某个列的并发，将ConcurrencyCheck特性添加到实体需要控制并发的**非主键属性**上即可。


## Q：数据库优化、索引、事务、视图、存储过程，全文检索，查询优化？
### A：


## Q：http 管道 httpmodule httphandle是做什么的？
### A：


## Q：堆栈区别？
### A：


## Q：数组是否值类型？
### A：


## Q：数组扩展长度内存操作原理 ？
### A：


## Q：数组和集合区别 ？
### A：


## Q：a=“123” b=“123”内存怎么分配，a=b时呢？
### A：


## Q：分布式锁原理？
### A：


## Q：redis五种数据类型？
### A：


## Q：rabbitMQ中交换机的理解？
### A：


## Q：抽象方法和virtual方法的区别？
### A：


## Q：const和readonly的区别？
### A：


## Q：扩展方法是动态还是静态？怎么写扩展方法？
### A：


## Q：IOC相关理解？
### A：


## Q：DDD的理解和认识？
### A：


## Q：.NET4.5 / 4.6以及历史版本的区别？
### A：


## Q：SQL分页怎么实现？
### A：


## Q：SQLPrameter的原理？
### A：


## Q：IIS应用程序池经典和继承的区别？
### A：


## Q：如何全局处理异常？
### A：


## Q：说说Webapi的restful风格的了解？post和put的区别？
### A：


## Q：nuget包上传管理流程？
### A：
