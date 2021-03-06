# Java

## Java概论

```scss
"Java体系"
    JavaEE(java platform enterprise edition) //企业版本:包含JavaSE
    JavaSE(java platform standard edition)   //标准版本:包含JavaME
    JavaME(java platform micro edition)      //微机版本

"Java工具"
    JDK(java development kit)     //开发工具:包含JRE
    JRE(java runtime environment) //运行环境:包含JVM
    JVM(java virtual machine)     //虚拟机

"Java命令"
    javac <.java源文件>                  //编译 compile
	javap <.class字节码文件>              //反编译	
    java <.class字节码文件>               //解析 execute
	java <.class字节码文件> <参数>         //命令行参数(传给主方法)
	java -enableassertions <>            //启动断言
    jshell                				 //交互模式
	javadoc -d <存储目录> <[包名][文件名]>  //生成文档

"文档注释常用标记"
    @author     //作者
    @version    //版本
	@deprecated //不推荐使用的方法
    @param      //方法参数
    @return     //方法返回值
    @exception  //抛出异常类型
    @throws		//抛出异常类型
"常用转义字符"
    \t	//tab
    \b	//退格
    \n	//换行
    \r	//回车
    \f	//换页
"Lambda表达式"
        (<参数集>)->{<表达式>} 
		<类|对象>::<方法> //单参调用已存在方法
"元注解"
	@Retention //注解保留阶段,参数使用枚举RetentionPolicy
        //RetentionPolicy.SOURCE //源文件
        //RetentionPolicy.CLASS  //字节码文件(默认)
        //RetentionPolicy.RUNTIME//运行时
	@Target //注解作用范围,参数使用枚举ElementType
        //ElementType.TYPE  //类,接口,枚举类,注解
        //ElementType.FIELD //字段,枚举常量
        //ElementType.METHOD//方法
	@Documented  //注解能够被javadoc打包至文档中
	@Inherited //父类注解被子类继承(没有的情况下)   
"常用注解"
    @Override //方法覆写
	@Deprecated //方法已过期 
	@Suppvisewarnings //压制警告  
	@FunctionalInterface //函数式接口      
"方法"
        //>方法重载 "参数的数量和类型不能完全相同"
        //>方法覆写 "重写父类方法,方法定义相同而实现不同"
        //>可变参数 "[param...] 底层由数组实现"
"包"
        //>查找类名的顺序	
            //1."当前包"
            //2."import语句"
            //3."java.lang包"
        //import语句
            import <包名>.<类名>;
            import <包名>.*; //星号(*)只能代替类,不能代替包
            import static <包名>.<类名>.*; //导入类中的静态成员(变量,方法)
"异常处理"
	Error //错误
	Exception //异常
	RuntimeException //运行时异常,选择性处理异常
	//非运行时异常: 必须捕获或者抛出异常,不然编译不通过
"泛型"
	//定义类和方法时不明确数据的类型,只有在创建对象或者调用方法时才将引用数据类型当作参数传递以此确定数据类型
	//>泛型擦除:编译后的.class文件不包含泛型数据
	//>通配符(?):可以匹配任意类型
	<? extends Type> //匹配Type及其子类
	<? super Type>   //匹配Type及其父类
"线程状态"
	新建状态>//new Thread();
	就绪状态>//start();yield()
	运行状态
	阻塞状态>//(1)等待阻塞:wait()
            //(2)同步阻塞:获取synchronized同步锁失败
            //(3)其他阻塞:sleep(),join()
	死亡状态
```

```scss
"面向对象的基本特征"
    继承 inherit       //子类获取父类的状态与行为
    封装 encapsulation //保留有限的外部接口，隐藏具体内部实施细节
    多态 polymorphic   //主要的表现形式为:编译时类型和运行时类型不一致
					  //子类只保留自身覆写内容和父类内容
					  //实现目的:一种行为的多种不同实现

"程序结构"
    1.顺序结构 //程序按照排列顺序依次执行
    2.选择结构 //程序按照不同的分支选择执行
    3.循环结构 //程序反复执行部分代码,直到条件判断为假是才停止循环
              //当型结构:先判断再循环
              //直到型结构:先循环再判断

"基础语法"
    标识符 identifier
		//所有用户自定义项的签名都遵循标识符的命名规则
		//标识符命名规则:由字母、数字、下划线、$以及Unicode 字符集中符号大于 0xC0 的所有符号组合构成且不能以数字开头
    保留字 reserved words //系统留用的标识符.
    关键字 keyword        //系统规定有特殊意义的保留字.
    表达式 expressions    //表达式是由变量，运算符等构造组件所构成,其结果返回一个值
    注释 comments
		//注释不会被编译器编译.
        //"// 单行注释"
        // "/* 多行注释 */"
        //"/** 文档注释 */"
    变量 variable
		//变量是内存引用的显相符号
        //>成员变量
			//实例变量(non-static)
			//类变量(static)
		//>局部变量
			//形式参数
			//方法局部变量
			//代码块局部变量
    常量 constant
		//常量是指在程序的整个运行过程中值保持不变的变量
    作用域 scope
		//变量或者对象的生命周期
        //变量的作用域在其声明语句的代码块之内
        //类的作用域由其佩戴的修饰符决定
    CLASSPATH
		//是JVM用来指示.class文件路径的环境变量
	不变类 
		//成员变量被final修饰,因此实例对象中的变量数值不可改变
		//包装类和java.lang.String类都是不变类
	函数式接口             //接口中只包含一个抽象方法
```



## 数据类型

> 基本数据类型

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
"基本数据类型基本规则"
	1.自动类型转换 //系统可以自动完成表数范围小的数据类型向表数范围大的数据类型的数据转换
    2.强制类型转换 //手动进行类型转换的方式,格式为:(<数据类型>)<数据>
    3.数据溢出    //数据超出了表数范围就会导致数据溢出
    4.自动类型提升 //1.表达式中byte,short和char将被自动提升成int
                 //2.表达式中所有数据类型将自动提升成当前表达式表数范围最大的数据类型
	5.自动装箱	  //自动完成基本数据类型转换成包装类型
	6.自动拆箱	  //自动完成包装类型装换成基本数据类型
"字面量"
	1.整型
        //默认类型 int;直面量可用下划线分割;
        //后缀L为long类型
        //前缀0x为十六进制
        //前缀0为八进制
        //前缀0b为二进制
	2.浮点型 
        //默认类型 double;
        //后缀f为float类型
        //后缀d为double类型
        //后缀e加数字为科学计数法
```

> 引用数据类型

```scss
"引用数据类型"
	//默认值都为null
	1.数组 //<数组名>.length 返回数组长度
	2.对象 
		//单继承
		//默认继承java.lang.Object
		//默认拥有无参构造函数
		//构造函数首行默认调用父类构造函数
		//this 指向对象本身的一个指针
		//super 指向直接父类的一个指针
	3.类
		//源文件中有且只有一个public类,且与源文件名称一致
		//>向上转型 子类实例可以应用父类类型
		//>向下转型 父类类型转换为实例类型
	4.String
		//连字符(+)将任意数据类型与String连接
	7.接口
		//字段默认[public static final]
		//方法默认[public abstract]
		//非抽象方法 <default>
		//抽象方法默认且只能被public修饰
		
	8.枚举类
		//由类封装而成
		//默认继承java.lang.Enum
		//枚举项就是枚举类的静态常量,其保存了当前类的实例
		//构造函数默认且只能被provate修饰
		//可以实现接口
		//被final修饰,所以不能被继承
	9.注解
		//由接口封装而成

```

## 语句

> 声明语句

```scss
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
		[public] class <name> [extends <父类>] [implements <接口集合>]{}
	5.成员内部类声明
		[修饰符] class <name> [extends <父类>] [implements <接口集合>]{}
	6.局部内部类
		class <name> [extends <父类>] [implements <接口集合>]{} //作用域在声明方法内
	7.匿名类
		new <接口名|抽象类名>(){<覆写方法>}
	8.对象声明
		<类名> <name> = new <类名>([param]);
	9.实例化成员内部类(non-static)
		new <外部类名>().new <内部类名>(); //non-static
		new <外部类名>.<内部类名>(); //static
	10.方法声明
		[修饰符] <void|返回值类型> <name>([param]) throws <异常集>{}
	11.构造函数声明
		[修饰符] <类名>([param]){}
	12.接口声明
		[public] interface <name>{[public abstract] <方法名>([param]);...}
	13.包声明
		package <name>;
	14.定义枚举类
        [public] enum <name>{
            [枚举项],[枚举项]...[枚举项]; 	 //[枚举项](<构造器参数>){<实现抽象方法>}

            [private] <构造函数> //默认且只能使用private

            [修饰符] <成员方法/变量|抽象方法>
        }
	15.自定义注解
        [public] @interface <name>{
            [public] <type> <name>() [default <默认值>];
        }
	16.异常处理语句
		try{<捕捉语句块>}catch(<异常类型> <name>){<异常处理语句块>}finall{<必定执行语句块>}
	17.抛出异常
		throw new <异常类型>();
	18.断言
		assert <判断语句>:<断言消息> //假则抛出AssertionError或者发送断言消息
	19.泛型
		//泛型类/接口 T是类型变量
        <name><T>{
            T fieldName;
            T methodName(T t);
        }
		//泛型方法
        <T> void <name>(T t){

        }
```

> 调用语句

```scss
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
	5.使用注解
		@<name>(<数据>) //有且只有一个参数并且参数名为value时
        @<name>(<注解参数>=<数据>,...)
    6.泛型
		new <name><实际类型>(); //类
		implements <name><实际类型> //接口
		<name>(<实参>); //方法 类型依据实参类型
```

> 控制流语句

```scss
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
```

> 块语句

```scss
	1.同步代码块
		synchronized(<锁对象>){<同步代码>}
	2.静态代码块
		static{} //总是在实例代码块执行之前执行
				 //只能初始化静态变量
				 //在一次解析过程中,同一个静态代码块只会执行一次
				   
	3.实例代码块
		{} //总是在构造器执行之前执行
```

## 修饰符

> 访问修饰符

| 访问修饰符                   |  类  | 包   | 子类 | 外   |
| :--------------------------- | :--: | :--- | :--- | :--- |
| public                       |  Y   | Y    | Y    | Y    |
| protected                    |  Y   | Y    | Y    |      |
| package-private(no modifier) |  Y   | Y    |      |      |
| private                      |  Y   |      |      |      |

> 非访问修饰符

```scss
static //1.不能直接使用实例数据(变量,方法)
	   //2.不能被实例化

final //1.变量的直面量不能被改变
	  //2.方法不能被覆写
	  //3.类不能被继承
	  //4.构造方法中可进行初始化

abstract //1.抽象类不能被实例化
		 //2.抽象方法只有定义没有实现

synchronized //同对象中所有同步方法只能被一个线程调用

volatile //变量只能从主内存读取(不能进行缓存读取)

native //调用本地系统方法

transient //不能被序列化
	  
```



## 运算符

> 算术运算符

```scss
	1.加法运算: +
	2.减法运算: -
	3.乘法运算: *
	4.除法运算: /
	5.取余运算: %
	6.自增运算: ++ //++i是先自增后取值,i++是先取值再自增
	7.自减运算: --
```

> 关系运算符

```scss

	1.相等运算: ==
	2.不等运算: !=
	3.大于运算: >
	4.小于运算: <
	5.大于等于: >=
	6.小于等于: <=
	>关系表达式返回布尔值
```

> 条件运算符

```scss

	1.与运算符: &&
	2.或运算符: ||
	3.非运算符: !
```

> 位运算符

```scss
	1.与运算符: & //都是1返回1
	2.或运算符: | //包含1返回1
	3.异或运算: ^ //相同返回0
	4.取反运算: ~ //取反加一
	5.左移运算: << //右边填充0 [左移n位相当于乘以2的n次方]
	6.右移运算: >> //左边填充原本符号位数值 [右移n位相当于除以2的n次方]
	7.无符右移: >>> //左边填充0
```

> 赋值运算符

```scss
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
```

> 其他运算符

```scss
"三元运算符"
<逻辑表达式> ? <真执行表达式> : <假执行表达式>
"类型比较运算符"
	<引用类型变量> instanceof <类,接口> //测试左边引用类型变量是否为右边类(包括其子类)的实例
"new运算符"
	1.实例化 instantiation //创建对象、分配内存、返回内存引用
	2.初始化 initialization//调用构造函数
```



## API解析

> **java.lang**

```scss
//java.base//

//java.lang
	"Object"      //所有类的最高父类
		clone     //return 此对象的拷贝
		equals    //compare(相等);return t|t|f
		getClass  //return Class类
		hashCode  //return 哈希值
		toString  //retrun .
		wait      //线程等待(直到被唤醒|倒计时完成)
		notify    //唤醒线程(当前监视器)
		notifyAll //唤醒所有线程(当前监视器)
	"Enum"                //[all] 枚举类直接父类
		values            //return 数组(所有枚举项名称)
		valueOf[S]        //param 枚举项名称,return 此枚举项
		ordinal           //return 当前枚举项的序数
		name              //return 当前枚举项的名称
		getDeclaringClass //return 枚举类名<包名+类名>
		toString          //默认返回枚举项名
	"Throwable"             //异常处理类的最高父类
		getMessage          //return 异常信息
		getLocalizedMessage //return 本地化异常消息
		printStackTrace     //print 异常信息和回溯
		getStackTrace
		setStackTrace
	"Number"   //所有数值类型的直接父类
		*Value //return 原始
	"CharSequence"[I] //所有字符类型的实现接口
	"Comparable"[I]    //able 比较器
		compareTo(T o) //compare(this:param);return -1|0|1
	"Iterable"[I]	   //able 迭代器
		iterator       //return Iterator对象
		spliterator[S] //return Spliterator对象
		forEach[S]	   //param  Consumer对象
	"Cloneable" //able clone
	"ClassLoader"                    //类加载器
        getResourceAsStream          //return InputStream;param String(路径/文件名)
        getSystemResourceAsStream[S] //return InputStream;param String(路径/文件名)
    "Runtime"               //运行时类
        availableProcessors //return 处理器数量
        freeMemory  		//return 可用内存
        maxMemory   		//return 最大内存
        totalMemory 		//return 总内存
	"System"              //系统类
		arraycopy[S]      //复制数组;param Object(入),int(start),Object(出),int(start),int(len)
		currentTimeMillis // return 当前时间(毫秒单位)
        setOut            //set(System.out);param PrintStream(打印位置)
		setErr            //set(System.err);param PrintStream(打印位置)
        setIn             //set(System.in);param InputStream (输出位置)
		//Field
			out[S]        //type PrintStream;输出流;
			err[S]        //type PrintStream;错误输出流;
			in[S]         //type InputStream;输入流;
//包装类
	"Byte,Short,Integer,Long,Float,Double"
		parse*[S]          //return 原始;param str
		valueOf[S]         //return 包装;param 原始|str
		decode[S]          //return 包装;param str
		compare[S]	       //compare(x:y);return -1|0|1
	"Integer,Long,Float,Double"
		max[S] //compare(x,y);return max 
		min[S] //compare(x,y);return min 
		sum[S] //return x+y
    "Float,Double"
		isFinite[S]    //compare(有限);
		isInfinite[+S] //compare(无限);
		isNaN[+S]      //compare(NaN);
	"Boolean,Character"
		valueOf[S]   //return 包装;param 原始|str
		parse?       //return 原始;param str
		?Value       //return 原始
//字符串处理
	"String"             //不变类
		//判断
        contains         //compare(包含);param CharSequence
		startsWith       //compare(头部包含);param String
        endsWith         //compare(结尾包含);param String
        contentEquals    //compare(等于);param CharSequence|StringBuffer
        equalsIgnoreCase //compare(等于~不考虑大小写)
        isBlank          //compare(为空或只包含空格);
        isEmpty          //compare(长度为0);
        matches          //compare(正则)
		indexOf          //compare(第一次出现);return int(索引);param String|int
        lastIndexOf      //compare(最后一次出现);return int(索引);param String|int
		//替换
		replace          //replace(old<new);param char|CharSequence;替换字符
		replaceAll       //replace(正则全部,param);param String
		replaceFirst     //replace(正则第一个,param);param String
		//分离
		split            //split(正则);return String[];分割字符串
		subSequence      //split(start,end);return CharSequence;param int(开始和结束索引)
		substring        //split(start,end);return String;param int(开始和结束索引)
		//合并
		concat           //concat(this+param);连接字符串
        repeat           //concat(this*param);param int(重复次数)
        join[S]          //concat(delimiter,ele...);param CharSequence
		//去空格
        trim             //trim(前后,小于'U+0020'的所有空格字符)
        strip            //trim(前后,空格)
        stripLeading     //trim(前,空格)
        stripTrailing    //trim(后,空格)
		//类型转换
		valueof          //transform(整|浮|布|char[]|char,String)
        copyValueOf[S]   //transform(char[],String)
        format[S]        //transform(格式字符串,String)
        getBytes         //transform(this|String|Charset,byte[])
        getChars         //transform(String,char[]);复制
		toCharArray      //transform(String,char[])
		//getter
		charAt           //return char;param int(索引)
		length           //return int(长度)
        lines            //return Stream类
		toLowerCase      //return 小写
		toUpperCase      //return 大写
		//constructor
		String(*)        //byte[],char[],int[],String,StringBuffer,StringBuilder
	"StringBuilder"  //可变类
	"StringBuffer"   //可变类,线程安全
		//功能
		append       //追加字符串;param *;
		delete       //删除字符串;param int(开始和结束索引);
		deleteCharAt //删除字符串;param int(开始索引);
		insert       //插入字符串;param int(索引),*;
		reverse      //翻转字符串
		trimToSize   //尝试减少存储数据的内存
		//set
		setCharAt    //set(索引处字符);param char
		setLength    //set(长度)
		charAt
		indexOf
		lastIndexOf
		replace
		subSequence
		substring
//数学计算
	"Math"                //数学运算;
	"StrictMath"          //严格数学运算;保证在各系统运算结果一致
		//运算
		abs[S]            //abs(param);param double|float|int|lang
		sqrt[S]           //sqrt(param);param double;平方根
		//安全运算
		addExact[S]       //exact(a+b);param int|lang;加法,溢出报错
		subtractExact[S]  //exact(a-b);param int|lang;减法,溢出报错
		multiplyExact[S]  //exact(a*b);param int|lang;乘法,溢出报错
		negateExact[S]    //exact(-param);param int|lang;取反,溢出报错
		decrementExact[S] //exact(param--);param int|lang;自减,溢出报错
		incrementExact[S] //exact(param++);param int|lang;自增,溢出报错
		//舍入法
		ceil[S]           //向上取整;param double
		floor[S]          //向下取整;param double
		round[S]          //四舍五入;param double|float;return long|int
		floorDiv[S]       //floor(a/b);param int|lang
		floorMod[S]       //floor(a%b);param int|lang
		//判断
		max[S]            //compare(a,b);return max;param double|float|int|lang
		min[S]            //compare(a,b);return min;param double|float|int|lang
		//类型转换
		toIntExact        //transform(long,int)
		//随机数
		random            //random(0-1);return double;随机数
//多线程
	"Runnable"[I] //able run();
	"Thread"
		//getter
        currentThread[S] //return Thread(当前执行线程)
        getId            //return long(ID)
        getName          //return String(名称)
        getPriority      //return int(优先级)
        getState         //return Thread.State(状态)
        getThreadGroup   //return ThreadGroup(线程组)
		//setter
        setDaemon        //set(守护线程)
        setName          //set(名称)
        setPriority      //set(优先级)
		//判断
        interrupted[S]   //transform(中断)
        isInterrupted    //transform(中断)
        isAlive          //transform(存在)
        isDaemon         //transform(守护线程)
		//功能
        start            //线程执行
        interrupt        //中断线程
        sleep            //线程休眠(倒计时完成)
        yield            //礼让线程
        join             //插队线程(直到运行结束|倒计时完成)
	//constructor
		Thread(*)        // param Runnable|ThreadGroup,Runnable|String(线程名)
//反射
	"Class" 
		getName           //return 类名
		getPackageName    //return 包名
		forName[S]        //return Class
		getPackage        //return Package
		getClassLoader    //return ClassLoader
		get[Declared]*[s] //*(Field,Method,Constructor,Annotation);public|Declared(全部)		
```

>**java.lang.annotation**

```scss
//java.base//

//java.lang.annotation
	"Annotation"[I]    //[all] 注解公共实现接口,反射相关
		annotationType //return 注解类型
```

>**java.lang.reflect**

```scss
//java.base//

//java.lang.reflect //反射相关
	"Field" //反射字段
        get //return 字段值;param Object(指定对象)
        set //set(旧,新);param Object(指定对象),Object(新值)
	"Method"          //反射方法
		invoke        //调用方法;param Object(指定对象),Object...(参数)
		setAccessible //set(设置可访问标志);param boolean
	"Constructor"         //反射构造函数
			setAccessible //set(设置可访问标志);param boolean
			newInstance   //实例化对象;param Object...(参数)
	"Executable" //Method,Constructor公共直接父类
	"Member"[I]           //Field,Method,Constructor,Executable公共实现类
		getName           //return 名称
		getModifiers      //return int(修饰符)
		(UP)getAnnotation //return Annotation
```

> **java.math**

```scss
//java.base//

//java.math
	"BigInteger" //任意大小整数
	"BigDecimal" //任意精度浮点数
```

> **java.util**

```scss
//java.base//

//java.util //工具类
	"Iterator"[I]	//顺序遍历
			hasNext //compare(下一个元素);return Boolean
			next	//return 下一个元素
	"Spliterator"[I] //并行遍历
	"Comparator"[I] //比较器 compare()
	"Scanner" 	//扫描器
        close   //关闭
        hasNext //compare(包含另一个输入)
        next    //return String;返回输入
        next*   //return *
	"Random" //随机数
			next* //return *(随机数);param int(随机数范围,只有*(int)才能添加参数)
//时间和日期
	"Calendar"[A] //日历
        add             //sum(Field,param);param int
		//判断
        after           //compare(this>Object);晚
        before          //compare(this<Object);早
		isLenient		//compare(宽松)
		//转换
        computeFields   //transform(this(毫秒),Field)
        computeTime     //transform(Field,毫秒)
		toInstant       //transform(this,Instant)
		//getter
        get             //return 时间|日期;param Field
        getCalendarType //return Field
        getInstance[S]  //return Calendar
        getTime         //return Date
        getTimeZone     //return TimeZone(时区)
		//setter
        set             //set(this);param Field,int(新值)
		setTime			//set(this);param Date
		setTimeInMillis //set(this);param long(毫秒)
        setLenient      //set(宽松|严格);param boolean
        setTimeZone     //set(时区);param TimeZone
	"Date"
		from //transform(Instant,Date)
		after,before,toInstant
//集合
	"Collection"[I] //集合公共实现接口
        add         //添加;param E
        addAll      //添加;param Collection
        clear       //删除所有
        remove      //删除;param Object(指定元素)
        removeAll   //删除;param Collection
		//判断
        contains    //compare(包含);param Object(指定元素)
        containsAll //compare(包含);param Collection(指定集合)
        isEmpty     //compare(空)
		//getter
        size        //return int(元素数量)
        stream[S]   //return Stream(链式流)
		iterator	//return Iterator(迭代器)
		//转换
        toArray     //transform(this,Object[]|T[]);pram [T]
	"List"[I] //有序,可重复,支持索引
        get         //return E(数据);param int(索引)
        set         //set(this,param);param int(索引),E(新值)
        sort        //排序;param Comparator
        subList     //split(start,end)
		//判断
        indexOf     //compare(首次出现);return int(索引);param Object(指定元素)
        lastIndexOf //compare(最后出现);return int(索引);param Object(指定元素)
		//重载方法
        add,remove  //param int(索引);
	"ArrayList"     //数组实现(查询快,增删慢)
	"Vector"        //数组实现,同步
	"LinkedList"    //双链表实现(查询慢,增删快)
        addFirst
        addLast
        getFirst
        getLast
        removeFirst
        removeLast
	"Set"[I]        //无序,不可重复,不支持索引
	"HashSet"       //哈系表实现
	"LinkedHashSet" //哈希表+链表实现
	"TreeSet"       //红黑树
//双列集合
	"Map"[I] //值可重复
		//判断
        containsKey   //compare(包含K)
        containsValue //compare(包含V)
        isEmpty       //compare(空)
		//遍历方式
        entrySet      //return Set(K,V)
        keySet        //return Set(K)
        values        //return Collection(V)
		//功能
        put           //添加元素(key相同时,新值替换旧值);param K,V
        putAll        //添加元素;param Map
        remove        //删除元素;param K
        clear         //删除所有
		//getter
        get           //return value;param Object(K)
        size          //return 元素数量
	"HashMap" 		//哈系表实现
	"LinkedHashMap" //哈系表+链表
	"TreeMap" 		//红黑树
	"Hashtable" 	//哈系表实现,同步
	"ConCurrentHashMap" //同步,高效
	"Properties<String,String>" //流
        load        //读取数据;param InputStream|Reader
        store       //写入数据;param OutputStream|Writer
        getProperty //获取元素
        setProperty //添加元素(调用HashTable.put)
//工具类
	"Arrays"      //数组工具类
		stream[S] //return Stream
		sort[S]   //排序
	"Collections" //集合工具类
```

>**java.io**

```scss
//java.base//

//java.io
	"Serializable"[I] //able 序列化
	"File" //文件/目录
        canExecute //compare(可运行)
        canRead //compare(可读)
        canWrite //compare(可写)
        exists //compare(存在)
        isDirectory //compare(目录)
        isFile //compare(文件)
        length //return long(文件长度)
	"InputStream" //字节输入流
		read 		 //读取数据;param byte[]
		readAllBytes //读取所有数据;return byte[]
		close
	"OutputStream" //字节输出流
		write //写入数据;param byte[]
		flush
	"Reader"  //字符输入流
		read  //读取数据;param char[]
	"Writer"  //字符输出流
		write //写入数据;param char[]|String
	"File*" //文件流(读取文件)
		//constructor param File
	"Buffered*" //缓冲流(缓冲数据)
		//constructor param 输入/输入流
	"Filter*" //过滤流
		//constructor param 输入/输入流
	"Print*" //打印输出流(只有输出)
		//constructor param File|输出|String
	"InputStreamReader"  //转换输入流(指定字符集)
		//constructor param 输入流,字符集
	"OutputStreamWriter" //转换输出流(指定字符集)
		//constructor param 输出流,字符集
```

> **java.util.function**

```scss
//java.base//

//java.util.function 函数式接口
	"Supplier" //生产者
		get
	"Consumer" //消费者
		accept
		andThen //组合操作
	"Predicate" //判断
		test
		and    //与
		or     //或
		negate //非
	"Function" //数据类型转换
		apply
		andThen //组合操作(之后)
		compose //组合操作(之前)
```

>**java.util.stream**

```scss
//java.base//

//java.util.stream
	"Stream"[I]  //链式流
        of       //return Stream;param T...
        concat   //return Stream;param Stream,Stream
        count    //return long(元素数量)
        forEach  //逐一处理;return void
        filter   //逐一过滤;
        map      //逐一映射;
        limit    //取用(0-param);param long
        skip     //跳过(0-param);param long
        distinct //去除重复值
        sorted   //排序

```

>**java.test**

```scss
//java.base//

//java.test
	"Format" //格式化公告直接父类
	"DateFormat" //Date格式化类
	"SimpleDateFormat" //Date格式化子类
```

> **java.sql**

```scss
//java.sql//

//java.sql
	"DriverManager"   //驱动管理对象
        getConnection //获取Connection对象

	"Connection"[I]      //数据库连接对象
        createStatement  //获取Statement对象
        prepareStatement //获取PreparedStatement对象
        setAutoCommit    //开启事务
        commit		     //提交事务
        rollback		 //回滚事务
		'close'

	"Statement"[I]      //执行[静态]sql的对象
        execute       	//执行任意sql语句
        executeUpdate 	//执行DML和DDL语句(return 影响行数)
        executeQuery  	//执行DQL语句(return ResultSet对象)
		'close'

	"PreparedStatement"[I] //执行[预编译]sql的对象(解决sql注入)
		set*(int,*)	  	   //为占位符赋值(param 位置,数值)
		execute            //执行任意sql语句
        executeUpdate      //执行DML和DDL语句(return 影响行数)
        executeQuery       //执行DQL语句(return ResultSet对象)

	"ResultSet"[I]     //结果集对象
        next           //游标向前移动一行
        get*(int)      // 获取数据(param 数据编号 start 1)
        get*(String)   //获取数据(param 列名)
		'close'
//javax.sql
	"DataSource"[I]   //数据库连接池
		getConnection //获取连接

```

## JDBC

```scss
//JDBC
	//导入mysql-connector
	1.注册JDBC驱动程序
		Class.forName("com.mysql.jdbc.Driver"); //可省略
	2.获取数据库连接对象
		Connection con=DriverManager.getConnection("jdbc:mysql://<域名[端口号]>/<数据库>","<用户名>","<密码>");
	3.获取执行sql语句对象
		PreparedStatement sta=con.prepareStatement("<sql语句>");
	4.占位符赋值
		sta.set*(<编号>,<数据>);
	5.执行sql
		int count=sta.executeUpdate(); //修改
	6.处理结果
		System.out.println(count);
	7.释放资源
		sta.close();con.close();
//数据库连接池
	1.创建数据库连接池对象
	//c3p0 
	//配置文件:1.c3p0.properties
	//		  2.c3p0-config.xml
	DataSource ds=new ComboPooledDataSource();
	//druid 
	//(配置文件 *.properties)
	DruidDataSourceFactory.createDataSource(<配置文件>)
	2.获取连接对象
	Connection con=ds.getConnection();
	//Spring JDBC
	new JdbcTemplate(ds);
//JdbcTemplate方法
	update //执行DML语句
	query  //查询,封装为JavaBean对象
	queryForMap //封装为map集合
	queryForList //封装为list集合
	queryForObject //封装为对象
```

## 面试题

```scss
//HashMap,Hashtable,ConcurrentHashMap三者之间的区别?
	//1.线程的安全性
		//HashMap 不同步
	//2.key和value的null
		//HashTable 不允许
	//3.高效性考虑
		//ConcurrentHashMap 高效,分流锁
	//4.扩容机制
		//HashMap *2
		//Hashtable *2+1
```

