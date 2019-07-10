## Q：面向对象的语言特性？

A：封装性、继承性、多态性。


## Q：在.NET中所有类的基类是？

A：Object。


## Q：在C#中，&和&&的区别？

A：&是按位与运算符(或取地址运算符)，&&是条件与运算符(也叫逻辑与运算符)。


## Q：委托声明的关键字是？

A：delegate。


## Q：在.NET中所有可序列化的类都被标记为？

A：Serializable。


## Q：一个类不想被继承应该？

A：标记为sealed。


## Q：简单描述CLR?

A：因为有了CLR的GC机制。正常情况下，.net会自动的帮忙释放内存,如果非托管代码，则需要手动释放，比如dataread、WebRequest。


## Q：如何对数组的元素进行倒序排列？

A：xx.Sort()后xx.Reverse()。


## Q：HTTP定义的基本的与服务器交互的方法有？

A：4种，分别是：GET获取、POST新建（也可以更新）、PUT更新、DELETE删除。


## Q：单点登录常用的实现方法有？

A：
1. 存放用户凭证在Cookie中，但是依赖Cookie不太安全而且无法跨域
2. 使用jsonp，和cookie差不多，虽然能解决跨域但加密算法泄露还是不安全
3. token，现在比较常见的方式，通过反复重定向来验证，因为所有信息都存在服务端，所以即使知道了加密算法也无法登录，比较安全。但是项目调用比较复杂。


## Q：什么是继承？什么是重载？

A：继承指子类可以拥有父类允许访问的属性、方法等。重载是一个函数通过参数类型或者数量区分不同的实现。


## Q：什么是接口类？

A：定义了一组行为的集合，其中的方法不能有具体实现。


## Q：什么是虚函数？什么是抽象函数?

A：虚函数是子类可以被override的（也可以不）函数，在父类中必须实现。抽象函数必须存在于抽象类中，不允许有具体实现，它的子类必须实现该方法（有点像接口中的方法）


## Q：在ASP.NET页面之间传递值除了Session、Cookie、Application，还有什么其他方法？

A：QueryString,POST,ViewData(基于字典),ViewBag(基于Dynamic)


## Q：ADO.net中常用的对象有哪些，其作用分别是什么？

A：SqlConnection连接数据库，SqlCommand执行sql语句，SQLDataAdapter查询数据后填充到DataSet，DataSet中包含DataTable存放数据。


## Q：什么是SQL注入，如何防止SQL注入攻击？

A：代码没有过滤特殊字符时，在执行sql语句处填入';等之类的字符来截断sql语句后再输入要执行的sql语句（删表等）来对数据库进行攻击。可以使用SQLParameter(把所有参数当字符串而不是关键字来处理)或者ORM来避免。


## Q：使用递归输出斐波那契数列，并输出第X项。

A：
```
int fb(int i)
{
	if(i<1) return 0;
	else if(i<=2) return i;
	else return fb(i-1)+fb(i-2);
}
```


## Q：将字符串www.abc.com逆序输出为”com.abc.www”。

A：str.Split('.').Sort().Reverse()


## Q：原生js的ajax？

A：em..........


## Q：在SQL环境下，写一个T-SQL函数，求从今天往后数的7000天，所在日期的当月有多少天？

A：
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

A：
```
create proc deltb
@tname char(20) --入参
as
declare @cmd char(50)='truncate table '+@tname
exec(@cmd)

exec deltb '表名'
```


## Q：请列出UML中几种视图的名称，并解释其中两种视图的作用？

A：em...............


## Q：请描述设计模式的含义，并写出你所了解的几中设计模式的名称？

A：通过面向对象特性更好的解耦代码，用过单例和工厂。


## Q：如何部署一个ASP.NET项目？

A：VS发布到文件夹，拷到服务器上，IIS指定目录并绑定IP（域名）。


## Q：写出验证中国移动手机号码的正则表达式？

A：1\d{10}	(不知道中国移动的开头是啥)


## Q：如何在所有页面加载时输出内容？

A：使用HTTPModule/中间件或者Filter。


## Q：什么是串行化？

A：将数据使用BinaryFormat从Stream保存到二进制文件，这种文件大小都是2的X次方。


## Q：用一个xml文件描述你自己？

A：
```
<me>
	<name>姓名</name>
	<sex>男</sex>
	<age>24</age>
</me>
```


## Q：判断一个字符串中出现次数最多的字符，并统计这个次数？

A：遍历字符串，创建字典，以char为key,value默认1，如果字典key中包含char则value+1。最后输出字典


## Q：什么是装箱和拆箱？

A：值类型到object是装箱，object到值类型是拆箱


## Q：C#中委托是什么？事件是不是一种委托？

A：委托是传递一个方法的引用，类似函数指针。事件是一种特殊的委托。


## Q：Override和重载的区别？

A：override是重写方法的关键字，重载指一个方法的不同实现。


## Q：什么叫应用程序域？

A：就是程序之间的边界，可以理解一个程序是一个应用程序域。


## Q：什么是不受管制的代码？

A：unsafe关键字里写的非托管代码。不经过CLR运行。可以写指针等骚操作。


## Q：string str = null和string str = “”的区别？
A：null表示不存在于内存中没有地址，“”表示存在于内存中的“”这个对象


## Q：描述class和struct异同？
A：class是引用类型放在堆上的，struct是值类型放在栈上的。


## Q：能用foreach遍历访问的对象需要实现_____接口或声明_____方法的类型。
A：IEnumerable接口、GetEnumerator()方法


## Q：GC是什么？为什么需要GC？
A：GC（Garbage Collector）是垃圾收集器。.net中垃圾收集器会自动对内存垃圾进行回收管理。


## Q：接口可否继承接口？抽象类可否实现接口？抽象类可否继承实体类？
A：接口可以继承接口。抽象类可以实现接口。抽象类可以继承实体类*（但是实体类必须有可访问的构造函数，所有类都无法继承只有private构造函数的实体类）*。


## Q：try里有一个return语句，那么finally中的代码会不会执行，在return前还是return后？
A：会，在return前执行。看反编译会发现finally的代码放在了函数出口之前。


## Q：两个对象值相同x.equals(y)==true，但可能有不同的hash code，这个说法对吗？
A：==比较地址，equals比较值*（等比地址Equals值）*。两个对象值相同则表示拥有相同的HashCode。


## Q：进程和线程的区别？
A：进程是系统进行资源分配和调度的单位；线程是CPU分配和调度的单位。一个进程可以有多个线程，这些线程共享这个进程的资源。*（进程是系统层面，线程是CPU层面。线程∈进程）*


## Q：堆和栈的区别？
A：栈上放的是由编译器自动分配释放的资源。堆上放的是代码中自己分配释放的资源，比如new对象时分配的内存空间。


## Q：请指出GAC的含义？
A：（Global Assembly Cache）全局程序集缓存。应该是指常用到的dll（比如System.Data,System.Collections）会缓存在windows一个指定的文件夹下，别的程序再使用的话就直接调用，不用重新加载了。em....没折腾过。


## Q：DataReader和DataSet有什么区别？
A：DataReader是读取数据库的（游标类似）。DataSet是用来存放数据的。


## Q：软件开发一般有几个阶段？每个阶段的作用？
A：需求分析，详细设计（架构设计），代码编写，测试，部署


## Q：什么是强类型？什么是弱类型？哪种更好？为什么？
A：需要在编译时定义变量类型的是强类型，比如User   user= new User();不需要指定类型的为弱类型如js  var user={};好坏看业务需求，各有千秋。


## Q：什么是反射？
A：在程序运行时动态获取程序集信息：接口、类、方法、属性等。


## Q：编程求从0-1000一共输出了多少个0？需要JS和C#？
A：em.........抖个机灵，js参照这个。
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


A：**isnull(列名，'指定值')可以使用coalesce(列名，'指定值')替换，结果一样**
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
A：静态变量。（static  object o=new Object();）


## Q：在.NET中引入ref和out关键字的根本原因是什么?
A：方法中操作的对象的地址和传入的参数地址不一致。ref修饰的变量在方法中改变值时候，实际参数也会改变。


## Q：.NET中的new关键字和override关键字的异同？
A：要重写的方法都需要virtual关键字，但是override是重写了父类的方法，调用的话是子类重写后的方法；new是重新写了一个同名的方法，隐藏了父类的方法。**如果把子类强制转换为父类的话new调用还是父类的方法，而override则调用子类重写的方法。**


## Q：.NET MVC框架是通过什么来解析HTTP请求的。
A：请求的method。。。。（一时半会没理解）


## Q：MD5实质是？
A：一种哈希（hash）散列**算法**。将字符串转换为字节数组后计算数组的hash值。


## Q：分布式分类？
A：
1. 应用分布式：程序部署在多台机器上
2. 缓存分布式：缓存部署在多台机器上
3. 数据库分布式：数据库部署在多台机器上
*我当时就这么瞎几把回答的*


## Q：后台接口如何鉴权？比如开发了一个后台管理系统，如何防止别人拿到你请求的接口恶意攻击？
A：OAuth使用accessToken访问。或者使用JWT


## Q：纯webapi项目，前端请求的用户信息存储在哪里？
A：web的话localStorage。不同端有不同的存储方式。


## Q：vue生命周期？
A：四种两类。（vue对象）创建前/后，挂载前/后（vue挂载到页面），更新前/后，销毁前/后。


## Q：多线程的线程同步如何实现？
A：
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
            //唤醒，继续执行刚才第一个线程输出，然后再自动挂起
            wh.Set();  
            //再次唤醒会执行第二个线程输出，然后再自动挂起，AutoResetEvent是按顺序来的
            //而ManuelResetEvent则在执行Set()后释放了所有挂起的线程
            //wh.Set(); 
            Console.ReadKey();
        }
        static void Waiter()
        {
            Console.WriteLine("Waiting...");
            wh.WaitOne(); //等待唤醒之后继续往下执行
            //AutoResetEvent和ManuelResetEvent相比相当于自动执行了这行
            //mre.Reset(); 
            Console.WriteLine("Notified");
        }
	   ```
	   
	   ManualResetEvent与AutoResetEvent区别是M的Set()方法一次释放所有挂起的线程，A在Set()之后又自动将后续线程挂起，需要再次Set()。A相当于M在WaitOne()之后执行M.Reset()

	   4. 线程池（em.....暂时看不懂搜出来的东西）

## Q：redis大数据并发（例如秒杀活动，放到redis时并发怎么处理）？
A：为redis加锁，别的进程判断如果锁存在则等待，直到锁被释放（通过时间戳等机制优化解决死锁）


## Q：Memochached（与redis区别）、UML用过吗？
A：用过Memochached，与redis的区别是redis有机制不是所有数据都放在内存中，会放磁盘一部分（重启不丢失）。redis支持更多数据类型（list,set,zset,hash）,redis是单线程。Memcached单个value最大只支持1MB，Redis最大支持512MB。UML没用过。


## Q：数据库锁了解过吗？
A：共享（S)锁、排它（X)锁、更新（U)锁。


## Q：EF避免脏读？
A：我们只需要在实体中增加一个byte[]类型的字段，并为其加上[Timestamp]特性:
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


## Q：什么是事务？
A：数据库的一种机制，在开启事务之后的操作中（如果发生了业务异常）可以将数据库回滚到开启事务之前的状态。


## Q：说说你知道的数据库优化方式？
A：
1. 建立索引
2. 使用存储过程
3. 使用视图
4. 优化查询语句


## Q：数据库索引使用需要注意什么？什么是视图？如何做查询优化？
A：
1. 一个表内索引最好不要太多，一般在主键和经常做where条件或者group by或者order by的列上创建索引，如果表数据太小索引反而会影响性能。
2. 视图是由一张或多张表联合查询出的虚拟表，复杂查询使用视图来代替联表查询会提升性能。
3. 查询语句优化一般尽量避免全表扫描，以下几点会全表扫描：
	1. 使用null判断，会全表扫描。
	2. <>(不等于)判断，会全表扫描。
	3. 使用or，会全表扫描。
	4. 左右模糊查询%xx%，会全表扫描。
	5. 尽量使用exists代替in，in会全表扫描。
	6. 尽量不要在where语句中判断运算后的结果，会全表扫描。

## Q：什么是跨域？如何解决跨域问题？
A：跨域是为了限制JS和Cookie只能访问同域名下的资源。解决可以使用CORS（Cross-Orign Resouces Sharing跨域资源共享），nuget有现成的包，原理是在HTTP报文头中添加标识来控制。比如：Access-Control-Allow:http://xx.com代表允许xx.com访问。


## Q：Http管道模型是什么？HttpHandler是什么？HttpModule是什么？中间件是什么？
A：
1. Http管道模型是指一个请求一层一层达到action，然后再一层一层出去的过程像个管道一样。
2. HttpHandle是ISAPI的aspnet_isapi.dll通过后缀名然后转发到不同的处理程序。比如.aspx会调用System.Web.UI.PageHandler处理页面。
3. HttpModule是请求在管道中经过的模块，可以自行编写实现身份认证、过滤器等功能。
4. 中间件类似于HttpModule，也是在请求在管道中经过的模块，区别是HttpModule基于事件（我是这么答的）。


## Q：堆栈区别？
A：堆上存放引用类型数据，需要手动开辟内存空间（new的时候）。栈上存放值类型数据，不需要手动开辟内存空间。


## Q：数组是否值类型？
A：数组都是引用类型，继承自System.Array，而Array继承自System.Object，众所周知值类型都是继承System.ValueType的。


## Q：数组扩展长度内存操作原理 ？
A：(这个面试官问的我到现在还没有理解他想问什么？可能是想问List在Add时候的扩容过程)
如果有人问**数组扩容**或者**List在Add时超出长度**在内存中的过程就回答：**如果新添加的元素超出数组长度则new一个更大的数组将原来数组copy过去。**


## Q：数组和集合区别 ？
A：数组声明时是定长的，且声明类型比如int[5]，内存上是连续存储的。
集合则可以一直添加元素，声明时不一定声明类型（使用泛型）比如List<object>。


## Q：a="123"; b="123";内存怎么分布，b=a时呢？
A：
1. “123”由于CLR的字符串驻留机制只存有一份。所以当a="123";b="123";时a和b都指向了"123"这个字符串的引用。
2. 当b=a时是把a的引用copy了一份给b。


## Q：分布式锁原理？
A：通过某种方式加一把锁，让分布式程序执行方法时获取锁，保证**同一个方法同一时刻只能被一台机器上的一个线程访问。**一般实现有：1. 通过数据库实现（加一条记录去读取之类的）。2. 通过redis实现。3. 通过Zookeeper（不知道是啥）。


## Q：redis五种数据类型？
A：
1. string
2. hash
3. list（值不唯一，可以通过pop实现简单消息队列）
4. set（值唯一）
5. zset


## Q：rabbitMQ中交换机的理解？
A：消息(Message)由Client发送，RabbitMQ接收到消息之后通过交换机转发到对应的队列上面。Worker会从队列中获取未被读取的数据处理。
RabbitMQ包含四种不同的交换机类型：
1. Direct exchange：直连交换机，转发消息到routigKey指定的队列
2. Fanout exchange：扇形交换机，转发消息到所有绑定队列（速度最快）
3. Topic exchange：主题交换机，按规则转发消息（最灵活）
4. Headers exchange：首部交换机 (未接触)
（抄的，只跑过收/发消息的demo）


## Q：const和readonly的区别？
A：const是编译时定好无法改变的。readonly归根结底还是对象中的属性，是动态的，只不过修饰为只读而已。


## Q：扩展方法是动态还是静态？怎么写扩展方法？
A：扩展方法是静态的，只能存在于静态类中。写法跟函数差不多，第一个参数必写为this 要扩展的类型 xxx，然后xxx则是调用扩展方法的对象本身，比如扩展一个string类的方法：
```
static void Output(this string str)
{
    Console.WriteLine(str);
    //"123".Output(); 执行后会输出123，
    //str对象就是调用方法的"123"字符串
}
```


## Q：IOC相关理解？
A：接口IA定义业务方法，A具体实现IA。通过IOC将实现类A注入到IA中，这样调用时虽然看起来是IA.方法()，其实执行的是实现类中的方法。实现了面向接口编程，降低对实现类的耦合。


## Q：DDD的理解和认识？什么是失血/贫血/充血/胀血模型？
A：可以通过聚合、实体等概念梗清晰的描述业务，底层的CQRS（读写分离）、UOW（UnitOfWork，自动实现事务）、仓储层都很好用。
1. 失血模型：领域模型只有get/set。没有任何实体业务逻辑，完全依赖service->DAL->domain调用。
2. 贫血模型：领域模型除了get/set后包含一些简单的实体组装逻辑，还是依赖service->DAL->domain调用。
3. 充血模型：领域模型包含DAL层的东西比如持久化，调用变为service->domain->DAL
4. 胀血模型：取消service层，直接通过domain->DAL来调用执行业务
（血越多领域层越复杂，对service层依赖越小）


## Q：.NET4.5 / 4.6以及历史版本的区别？
A：
- .NET 3.0 引入WPF、WCF、WF。使用CLR 2.0，对应C# 3.0；
- .NET 3.5 引入Linq、EF、扩展方法、特性、Lambda。使用CLR 2.0，对应C# 3.0；
- .NET 4.0 增加了并行的支持。使用CLR 4.0，对应C# 4.0；
- .NET 4.5 增加了Task异步编程模型（async/await）。使用CLR 4.0，对应C# 5.0；
- .NET 4.6 优化（好像同时发布/引入了ASP.NET Core）。使用CLR 4.0，对应C# 6.0；
- .NET 4.6.2 对应C#7.0


## Q：SQL分页怎么实现？
A：
1. select top 页大小 from x where id not in(select top 页大小x(页码-1) id from x) 不推荐使用因为in会造成全表扫描。
2. ```
   select * from (
   		select *,ROW_NUMBER() OVER(order by id) as RowId from x
   	) as t
   	where t.RowId between 页大小x(页码-1) and 页大小x页码
   ```


## Q：SQLParameter的原理？
A：把所有参数当字符串而不是关键字来处理。


## Q：IIS应用程序池经典模式和集成模式区别？
A：
- 经典模式：兼容IIS6.0，继续通过C盘下aspnet_isapi.dll来处理请求。
- 集成模式：使用IIS和ASP.NET的集成请求处理管道来处理请求。


## Q：如何全局处理异常？
A：使用中间件记录处理异常，或者使用ExceptionFilter来捕获全局异常。


## Q：说说Webapi的restful风格的了解？post和put的区别？
A：对同一个接口地址通过不同的请求Method编写不同的逻辑。一般包括四种：
1. get：查询
2. post：添加
3. put：更新
4. delete：删除
因为put一般代表更新操作，所以是幂等的，更新一万次对象还是存在。而post则不是幂等的，多次post会创建多个数据。

## Q：nuget包上传管理流程？
A：
1. nuget官网下载nuget.exe
2. cmd命令 nuget pack生成x.nupkg文件
3. 登录nuget官网创建一个密钥
4. cmd命令 nuget push x.nupkg 密钥 -Source https://api.nuget.org/v3/index.json
5. 上传完成，可在VS中搜索到