# Java

>
>
>Java 是由 Sun Microsystems 公司于 1995 年推出的一门面向对象程序设计语言。2010 年 被Oracle 公司收购

## Java概论

```scss
//Java体系
    JavaEE(java platform enterprise edition) //企业版本:包含JavaSE
    JavaSE(java platform standard edition)   //标准版本:包含JavaME
    JavaME(java platform micro edition)      //微机版本

//Java工具
    JDK(java development kit)     //开发工具:包含JRE
    JRE(java runtime environment) //运行环境:包含JVM
    JVM(java virtual machine)     //虚拟机

//Java命令
    javac <.java源文件>                  //编译 compile
    java <.class字节码文件>               //解析 execute
	java <.class字节码文件> <参数>         //命令行参数(传给主方法)
    jshell                				//交互模式
	javadoc -d <存储目录> <[包名][文件名]> //生成文档

//面向对象的基本特征
    继承 inherit       //子类获取父类的状态与行为
    封装 encapsulation //保留有限的外部接口，隐藏具体内部实施细节
    多态 polymorphic   //同一个行为具有多个不同表现形式

//程序结构
    1.顺序结构 //程序按照排列顺序依次执行
    2.选择结构 //程序按照不同的分支选择执行
    3.循环结构 //程序反复执行部分代码,直到条件判断为假是才停止循环
              //当型结构:先判断再循环
              //直到型结构:先循环再判断

//基础语法
    标识符 identifier     //所有用户自定义项的签名都遵循标识符的命名规则
                         "标识符命名规则:由字母、数字、下划线、$以及Unicode 字符集中符号大于 0xC0 的所有符号组合构成且不能以数字开头"
    保留字 reserved words //系统留用的标识符.
    关键字 keyword        //系统规定有特殊意义的保留字.
    表达式 expressions    //表达式是由变量，运算符等构造组件所构成,其结果返回一个值
    注释 comments         //注释不会被编译器编译.
                         "// 单行注释"
                         "/* 多行注释 */"
                         "/** 文档注释 */"
    变量 variable         //变量是内存引用的显相符号
						 "成员变量"
						 "类变量"
						 "局部变量"
    常量 constant         //常量是指在程序的整个运行过程中值保持不变的变量
    作用域 scope          //变量或者对象的生命周期
                         "变量的作用域在其声明语句的代码块之内"
                         "类的作用域由其佩戴的修饰符决定"
    CLASSPATH            //是JVM用来指示.class文件路径的环境变量
//文档注释常用标记
    @author     //作者
    @version    //版本
	@deprecated //不推荐使用的方法
    @param      //方法参数
    @return     //方法返回值
    @exception  //抛出异常类型
    @throws		//抛出异常类型
//常用转义字符
    \t	//tab
    \b	//退格
    \n	//换行
    \r	//回车
    \f	//换页

```

## 数据类型

| 基本数据类型 | 取值范围    | 默认值   | 内存 | 包装类              |
| :----------- | :---------- | :------- | :--- | :------------------ |
| byte         |             | 0        | 1    | java.lang.Byte      |
| short        |             | 0        | 2    | java.lang.Short     |
| int          |             | 0        | 4    | java.lang.Integer   |
| long         |             | 0L       | 8    | java.lang.Long      |
| boolean      |             | false    | 1    | java.lang.Boolean   |
| char         | UTF-16      | '\u0000' | 2    | java.lang.Character |
| float        |             | 0.0f     | 4    | java.lang.Float     |
| double       | true、false | 0.0d     | 8    | java.lang.Double    |

```scss
//基本数据类型基本规则
	1.自动类型转换 //系统可以自动完成表数范围小的数据类型向表数范围大的数据类型的数据转换
    2.强制类型转换 //手动进行类型转换的方式,格式为:(<数据类型>)<数据>
    3.数据溢出    //数据超出了表数范围就会导致数据溢出
    4.自动类型提升 //1.表达式中byte,short和char将被自动提升成int
                 //2.表达式中所有数据类型将自动提升成当前表达式表数范围最大的数据类型
	5.自动装箱	  //自动完成基本数据类型转换成包装类型
	6.自动拆箱	  //自动完成包装类型装换成基本数据类型
//字面量
	1.整型  //默认类型 int;直面量可用下划线分割;
           "后缀L为long类型"
           "前缀0x为十六进制"
           "前缀0为八进制"
           "前缀0b为二进制"
	2.浮点型 //默认类型 double;
			"后缀f为float类型"
			"后缀d为double类型"
			"后缀e加数字为科学计数法"
```

```scss
//引用数据类型
	"默认值都为null"
	1.数组 //<数组名>.length 返回数组长度
	2.对象 
		"单继承"
		"默认继承java.lang.Object"
		"默认拥有无参构造函数"
		"构造函数首行默认调用父类构造函数"
		"this 保存当前实例引用"
		"super 保存this的父类"
	3.类
		"源文件中有且只有一个public类,且与源文件名称一致"
		>向上转型 "子类实例可以应用父类类型"
		>向下转型 "父类类型转换为实例类型"
	4.String
		"连字符(+)将任意数据类型与String连接"
	5.方法
		>重载方法 "参数的数量和类型不能完全相同"
		>方法覆写 "方法定义相同,方法实现不同"
		>可变参数 "[param...] 底层由数组实现"
	6.包
		>查找类名的顺序	1."当前包"
                         2."import语句"
                         3."java.lang包"
		"import 引入包"
	7.接口
		"字段默认[public static final]"
		"方法默认[public abstract]"
		"非抽象方法 <default>"

```



## 语句

```scss
//声明语句
	1.局部变量声明
		var <name> = <value>; //使用var定义的局部变量类型由编译器通过直面量自动推断  
		<type> <name> [= <value>]; 
	2.成员变量声明
		[修饰符]<type> <name> [= <value>];
	3.数组声明
		<type> [] <name> = new <type> [len];
		<type> [] <name> = new <type> []{<数据集合>};
		<type> [] <name> = {<数据集合>};
	4.类声明
		[public] class <name> extends <父类> implements <接口集合>{}
	5.对象声明
		<类名> <name> = new <类名>([param]);
	6.方法声明
		[修饰符] <void|返回值类型> <name>([param]){}
	7.构造函数声明
		[修饰符] <类名>([paramS]){}
	8.接口声明
		[public] interface <name>{[public abstract] <方法名>([param]);...}
	9.包声明
		package <name>;
//调用语句
	1.数组调用
		<name>[index];
	2.实例调用
		<name>.<字段>;
		<name>.<方法>([param]);
	3.类调用
		<类名>.<字段>;
		<类名>.<方法>([param]);
	4.包引用
		import <包名>;
//控制流语句
	1.决策语句
		//if-else
        if(<逻辑表达式>){<真执行语句块>}else{<假执行语句块>};
		//switch
        switch(<逻辑表达式>){
            case <匹配值> :[执行表达式][break;]
            ... ...
            default:[执行表达式]
        };
	2.循环语句
		//do-while
		do{<执行语句块>}while(<逻辑表达式>)
		//while
		while(<逻辑表达式>){<执行语句块>}
		//for
		for([初始化表达式][逻辑表达式][自增表达式]){<执行语句块>}
		//for-each
		for(<数据元素> : <可迭代引用类型数据>){<执行语句块>}
	3.分支语句
		//break
		break [标签名]; //跳出当前循环语句
		//continue
		continue [标签名]; //跳过当前迭代
		//return
		return [数值]; //跳出当前方法并返回数据
	4.标签语句
		//lable
		<标签名> : <循环语句> //配合分支语句使用

//块语句
	1.同步代码块
	synchronized(<锁对象>){<同步代码>}
	2.静态代码块
	static{} //随着类的加载而执行，而且只执行一次
```

## 运算符

```scss
//算术运算符
	1.加法运算: +
	2.减法运算: -
	3.乘法运算: *
	4.除法运算: /
	5.取余运算: %
	6.自增运算: ++ //++i是先自增后取值,i++是先取值再自增
	7.自减运算: --
//关系运算符
	1.相等运算: ==
	2.不等运算: !=
	3.大于运算: >
	4.小于运算: <
	5.大于等于: >=
	6.小于等于: <=
	>关系表达式返回布尔值
//条件运算符
	1.与运算符: &&
	2.或运算符: ||
	3.非运算符: !
//位运算符
	1.与运算符: & //都是1返回1
	2.或运算符: | //包含1返回1
	3.异或运算: ^ //相同返回0
	4.取反运算: ~ //取反加一
	5.左移运算: << //右边填充0 [左移n位相当于乘以2的n次方]
	6.右移运算: >> //左边填充原本符号位数值 [右移n位相当于除以2的n次方]
	7.无符右移: >>> //左边填充0
//赋值运算符
	1.赋值运算: =
	2.加法赋值: +=
	3.减法赋值: -=
	4.乘法赋值: *=
	5.除法赋值: /=
	6.取余赋值: %=
	7.位与赋值: &=
	8.位或赋值: |=
	9.异或赋值: ^=
   10.取反赋值: ~=
   11.左移赋值: <<=
   12.右移赋值: >>=
//三元运算符
<逻辑表达式> ? <真执行表达式> : <假执行表达式>
//类型比较运算符
	<实例对象> instanceof <类> //测试左边对象是否为右边类的实例
//new运算符
	1.实例化 instantiation //创建对象、分配内存、返回内存引用
	2.初始化 initialization//调用构造函数
```

## API解析

```scss
//java.util
	Arrays //数组的工具类
//java.sql
	DriverManager     //驱动管理对象
        getConnection //获取Connection对象

	Connection[I]        //数据库连接对象
        createStatement  //获取Statement对象
        prepareStatement //获取PreparedStatement对象
        setAutoCommit    //开启事务
        commit		     //提交事务
        rollback		 //回滚事务
		'close'

	Statement[I]      //执行[静态]sql的对象
        execute       //执行任意sql语句
        executeUpdate //执行DML和DDL语句(return 影响行数)
        executeQuery  //执行DQL语句(return ResultSet对象)
		'close'

	PreparedStatement[I] //执行[预编译]sql的对象(解决sql注入)
		set*(int,*)	  //为占位符赋值(param 位置,数值)
		execute       //执行任意sql语句
        executeUpdate //执行DML和DDL语句(return 影响行数)
        executeQuery  //执行DQL语句(return ResultSet对象)

	ResultSet[I]     //结果集对象
        next         //游标向前移动一行
        get*(int)    // 获取数据(param 数据编号 start 1)
        get*(String) //获取数据(param 列名)
		'close'
```

```scss
//JDBC
	1.注册JDBC驱动程序
		Class.forName("com.mysql.jdbc.Driver"); //可省略
	2.获取数据库连接对象
		Connection con=DriverManager.getConnection("jdbc:mysql://<域名[端口号]>/<数据库>","<用户名>","<密码>");
	3.获取执行sql语句对象
		Statement sta=con.createStatement();
	4.执行sql
		int count=sta.executeUpdate("<sql语句>"); //修改
	5.处理结果
		System.out.println(count);
	6.释放资源
		sta.close();con.close();
```

