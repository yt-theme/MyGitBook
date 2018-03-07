### 数据库
1. Database						   数据库
2. database management system (DBMS)  数据库管理软件
3. 数据库语法

#### 概念
库 、表、列
#### 普通进程与系统服务
普通进程会在登录后启动
系统服务在登录之前已启动

<br/>
<br/>
<br/>

1. 连接名
2. 主机名ip地址
3. 用户名
4. 密码

<br/>
<br/>
<br/>
新建数据库
1. 数据库名
2. 字符集UTF-8
3. 排序规则 *

<br/>
新建表
1. 
<br/>

主键

<br/>

数据类型
1. 文本
    1. CHAR 最多255字节定长字符串
    2. VARCHAR 最多255字节可变长字符串
    3. TEXT 最长64K字符变长文本
    4. MEDUIMTEXT 最大长度16k字符变长文本
    5. LONGTEXT 最大长度为4gb字符变长文本
2. 整数
	1. tinyint 1字节有符号值-128 - 127无符号值0 - 255
	2. smallint 1字节有符号值-32768 - 32767无符号值0 - 65535
	3. mediumint 3字节
	4. int 4字节
	5. bigint 8字节
3. 小数
	1. decimal 精确存储小数 内部字符串存储
	2. float 4字节单精度 近似存储 效率比decimal高
	3. double 8字节双精度 近似存储 效率比decimal高
4. 日期时间
	1. DATE 4字节 1000-01-01 - 9999-12-31
	2. TIME 3字节 -838:59:59 - 838:59:59
	3. DATETIME 8字节 1000-01-01 00:00 --9999-12-31 23:59:59
5. 二进制大数据
	1. TITYBLOB 最大长度为255字节
	2. BLOB 最大长度为64kb
	3. MEDUIMBLOB 最大长度为16mb
	4. LONGBLOB 最大长度为4gb
bit ->bool
<br/>

长度

<br/>

存储引擎

InnoDB

<br/>

#### MySQL
1. 用单引号
2. 写不敏感

检索数据
```
select * from T_Student
select Name,Age from T_Student
select Name as 姓,Age as 年 from T_Student
select 1+1
select now() # 当前时间
select Age+10 from T_Student
select 1=1 # 1
select 1=2 # 0
```
insert into   插入数据
```
#插入
insert into T_Student(Id,Name,Age) value(4,1,'姓')
# value   分别给Id,Name,Age赋值
```
update   更新数据
```
update T_Student set age=50,Name="aaaaaaaa"
select * from T_Student #看到结果
```
```
update T_Student set Age=Age+1 # a+=1
```
有条件的更新 更新name='he'的数据
```
update T_Student set Age=10 where Name='he'
```
```
update T_Student set age=10 where Name='he' or Age<25 # he或25
```
delete 删除数据 不删除表
```
# 删除条件
delete from T_Student where Age>20 or Age<1
# 删除所有
delete from T_Student
```
删除表
```
drop table T_Student
```
#### 聚合函数
> MAX MIN AVG SUM COUNT

```
#选取最大Age的数据
select max(Age) from T_Student
select max(Salary) as 最高工资,min(Salary) 最低工资 from T_Student where Age>=25 # 不写as也可
```
```
# 个数
select count(*) from T_Student # 所有最高个数
select count(Name) from T_Student # Name个数
select count(Name) from T_Student where Age>25 # Name中的Age>25数量
```
#### 空值处理
null

表示不知道的值
```
select null # null
```
```
select null=null # null
```
```
select 1+null # null
select 1=null # null
```
is null

is not null
```
select * from T_Student where Name is not null # 查询Name不为null数据
```
#### 数据排序
order by
> 必须在select末尾
> 默认升序

升序->小到大ASC

降序->大到小DESC
```
select * from T_Student order by Age ASC
```

<br/>
#### 分页
> 获取查询范围内数据

limit 放 select 后

	limit 首行行号,要返回的结果集的最大数目
```
select * from T_Student limit 2,3 #从第二条数据开始的三条数据
```
order by
```
select * from T_Student order by Age Desc limit 2,3 # 降序
```
#### group by
将检索结果划分多个组
```
select Age from T_Student group by Age # 按Age分组
select Age,AVG(Age) from T_Student group by Age
```
#### 外键约束

#### 主键
> 唯一标识,不重复的列<br/>
> 统一用没有任何意义的字段

1. 业务主键 有某种意义
2. 逻辑主键 没意义的键只给程序看

<br/>
#### 表间关联、外键
解决重复

<br/>
#### 通配符
like
>性能差<br/>
>全表扫描可能卡死

```
# _ 通配符匹配单个字符
select * from T_Student where Name like '_a' # 以任意一个单一字符串开头以a结尾
```
```
# % 匹配任意多个字符
select * frin T_Student where Name like 'o%'
```
```

```