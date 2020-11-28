# MYSQL 

## 服务命令

```scss
//Windows
1.使用”services.msc”打开服务管理器

2.
[启动] new start mysql
[停止] new stop mysql
```

```scss
//Linux
[启动] service mysql start
[停止] service mysql stop
[重启] service mysql restart
[状态] service mysql status
```

```scss
//登录数据库
mysql -h <地址> -u <用户名> -p <密码>
```

## 库命令

```scss
//库命令
create database; <库名> //创建
drop database; <库名> //删除
use <库名>; //选择
show databases; //查询(所有库)
show create database <库名> //查询(库定义)
```

## 表命令

```scss
//表命令
//创建
create table <表名>(列名 数据类型 [列级别约束条件],... ...[表级别约束条件]);
//删除
drop table [if exists]<表名1,表名2...>;
//删除(外键约束)
alter table <表名> drop foreign key <外键约束名>

//修改(表名)
alter table <表名> rename [to] <新表名>;
//修改(表的存储引擎)
alter table <表名> engine=<引擎名(默认:InnoDB)>;
//查询(所有表)
show tables;
//查询(表结构)
describe <表名>; desc <表名>;
//查询(表定义)
show create table <表名\g>;
```

## 字段命令

```scss
//字段命令
//增加
alter table <表名> add <列名><数据类型>[约束条件][first|after 已存在列名];
//删除
alter table<表名> drop <列名>;
//修改
alter table <表名> modify <列名><数据类型>[first|after 已存在列名];
alter table <表名> change <列名> <新列名><数据类型>;
```

## 记录命令

```scss
//记录命令
//添加记录
insert into <表名>(列名1,列名2,...) values(数据1,数据2...),(数据1,...);
```



## 约束

```mysql
//非空约束
not null

//唯一约束
unique

//默认约束
default 默认值

//自增约束:表唯一且修饰主键列(整数类型)
auto_increment

//外键约束:从表(非空)必须等于主表列的某个值
[constraint <约束名>]
foreign key (列名1,列名2,...)
references <主表名>(列名1,列名2,...)

//主键约束:唯一且非空
primary key

//联合主键:多列唯一且非空
[constraint <约束名>]
primary key(列名1,列名2,...)
```

## 数据类型

```mysql
//整数
tinyint //1
smallint //2
mediumint //3
int(integer) //4
bigint //8
```

```mysql
//小数
float //4
double //8
[decimal(m,d),dec] /m+2
```

```mysql
//字符串
char(M) //M
varchar(M) //L+1
tinytext //L+1
text //L+2
mediumtext //L+3
longtext //L+4
enum
set
```

```mysql
//二进制字符串
bit(M) //M+7/8
binary(M) //M
varbinary(M) //M+1
tinyblob(M) //L+1
blob(M) //L+2
mediumblob(M) //L+3
longblob(M) //L+4
```

```mysql
//日期/时间
year //[YYYY] 1
time //[HH:MM:SS] 3
date //[YYYY-MM-DD] 3
datetime //[YYYY-MM-DD HH:MM:SS][8][1000-01-01~9999-12-31 23:59:59]
timestamp //[YYYY-MM-DD HH:MM:SS][4][1970-01-01 00:00:01~2038-01-19 03:14:07 UTC]
```

## 运算符

```mysql
//算术运算符
[加法运算] +
[减法运算] -
[乘法运算] *
[除法运算] \
[求余运算] %
```

```mysql
//比较运算符
[等于] =
[安全等于] <=>
[不等于] <>,!=
[大于] >
[大于等于] >=
[小于] <
[小于等于] <=
[空] is null
[非空] is not null
[最小值] least(集合)
[最大值] greatest(集合)
[之间] between <min> and <max>
[包含] in(集合)
[不包含] not in(集合)
[模糊匹配] like ('%'多匹配)('_'单匹配)
[正则匹配] regexp
```

```mysql
//逻辑运算符
[非---] not,!
[与---] and,&&
[或---] or,||
[异或] xor (一项为假则为假)
```

```mysql
//位运算符
[或--] |
[与--] &
[异或] ^
[左移] <<
[右移] >>
[取反] ~
```

## 函数