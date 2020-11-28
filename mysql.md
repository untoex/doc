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
//创建表
create table <表名>(列名 数据类型 [列级别约束条件],... ...[表级别约束条件]);
//删除表
drop table [if exists] <表集合>;
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
//增加字段
alter table <表名> add <列名><数据类型>[约束条件][first|after 已存在列名];
//计算字段(可用于创建表,增加字段)
<列名> <数据类型> [约束条件] [generated always] as (<求值表达式>) [virtual | stored]
//删除字段
alter table<表名> drop <列名>;
//修改字段
alter table <表名> modify <列名><数据类型>[first|after 已存在列名];
alter table <表名> change <列名> <新列名><数据类型>;
```

## 记录命令

```scss
//记录命令
//插入记录
insert into <表名>(列名集合) values(数据集合),()...;
insert into <表名>(列名集合) {<子查询>}
//删除记录
delete from <表名> [where {判断语句}]
//更新记录
update <表名> set {<字段名>=<新记录>},{}... where {判断语句};
```

```scss
//记录查询命令
//查询
select {*|<字段集合>} from <表集合>
//不重复查询
select distinct <字段名> from <表名>
//合并查询
select {*|<字段集合>} from <表名> union [all(可重复)] {<查询语句>}
//内连接查询 (两边都满足条件)
{查询语句} inner join <表名2> on <判断表达式>
//左外连接查询(左表所有记录,右表满足条件)
{查询语句} left [outer] join <表名2> on <判断表达式>
//右外连接查询(右表所有记录,左表满足条件)
{查询语句} right [outer] join <表名2> on <判断表达式>
//子查询(可以添加到select,update和delete语句中)
any(<查询语句>) //任一
some(<查询语句>) //任一
all(<查询语句>) //所有
exists(<查询语句>) //存在
in(<查询语句>) //包含
//其他命令
//判断
where <表达式> //分组之前
having <表达式> //分组之后
//分组(必须配合集合函数使用)
group by <字段名>,<>...[with rollup(统计数目)]
//排序
order by <字段名 asc|desc(降序)>,<>...
//分页 (页数-1)*行数=起始行
limit <[起始行],行数>
//别名
<表名|字段名> [as] <别名>
```

## 其他命令

```scss

```



## 约束

```scss
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
foreign key (<字段集合>) references <主表名>(<字段集合>)
//主键约束:唯一且非空
primary key
//联合主键:多列唯一且非空
[constraint <约束名>] primary key(<字段集合>)
```

## 数据类型

```scss
//整数
tinyint //1
smallint //2
mediumint //3
int(integer) //4
bigint //8
```

```scss
//小数
float //4
double //8
[decimal(m,d),dec] /m+2
```

```scss
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

```scss
//二进制字符串
bit(M) //M+7/8
binary(M) //M
varbinary(M) //M+1
tinyblob(M) //L+1
blob(M) //L+2
mediumblob(M) //L+3
longblob(M) //L+4
```

```scss
//日期/时间
year //[YYYY] 1
time //[HH:MM:SS] 3
date //[YYYY-MM-DD] 3
datetime //[YYYY-MM-DD HH:MM:SS][8][1000-01-01~9999-12-31 23:59:59]
timestamp //[YYYY-MM-DD HH:MM:SS][4][1970-01-01 00:00:01~2038-01-19 03:14:07 UTC]
```

## 运算符

```scss
//算术运算符
[加法运算] +
[减法运算] -
[乘法运算] *
[除法运算] \
[求余运算] %
```

```scss
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
[范围内] between <min> and <max>
[包含] in(集合)
[不包含] not in(集合)
[模糊匹配] like ('%'多匹配)('_'单匹配)
[正则匹配] regexp
```

```scss
//逻辑运算符
[非---] not,!
[与---] and,&&
[或---] or,||
[异或] xor (一项为假则为假)
```

```scss
//位运算符
[或--] |
[与--] &
[异或] ^
[左移] <<
[右移] >>
[取反] ~
```

## 函数

```scss
//集合函数
max(字段名) //最大值
min(字段名) //最小值
count(字段名) //行数
sum(字段名) //总和
avg(字段名) //平均数
```

