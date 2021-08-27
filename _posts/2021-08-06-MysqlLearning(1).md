MySQL 学习笔记<br>
==============<br>
了解数据库<br>
-----------<br>
#什么是数据库<br>
数据库（Database）是按照数据结构来组织、存储和管理数据的仓库。<br>
每个数据库都有一个或多个不同的 API 用于创建，访问，管理，搜索和复制所保存的数据。<br>
我们也可以将数据存储在文件中，但是在文件中读写数据速度相对较慢。<br>
所以，现在我们使用关系型数据库管理系统（RDBMS）来存储和管理大数据量。所谓的关系型数据库，是建立在关系模型基础上的数据库，借助于集合代数等数学概念和方法来处理数据库中的数据。<br>
MySQL<br>
MySQL是最流行的关系型数据库管理系统，在 WEB 应用方面 MySQL 是最好的 RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。<br>
MySQL是一个关系型数据库管理系统，由瑞典 MySQL AB 公司开发，目前属于 Oracle 公司。MySQL 是一种关联数据库管理系统，关联数据库将数据保存在不同的表中，而不是将所有数据放在一个大仓库内，这样就增加了速度并提高了灵活性。<br>
MySQL 是开源的，目前隶属于 Oracle 旗下产品。<br>
MySQL 支持大型的数据库。可以处理拥有上千万条记录的大型数据库。<br>
MySQL 使用标准的 SQL 数据语言形式。<br>
MySQL 可以运行于多个系统上，并且支持多种语言。这些编程语言包括 C、C++、Python、Java、Perl、PHP、Eiffel、Ruby 和 Tcl 等。<br>
MySQL 对PHP有很好的支持，PHP 是目前最流行的 Web 开发语言。<br>
MySQL 支持大型数据库，支持 5000 万条记录的数据仓库，32 位系统表文件最大可支持 4GB，64 位系统支持最大的表文件为8TB。<br>
MySQL 是可以定制的，采用了 GPL 协议，你可以修改源码来开发自己的 MySQL 系统。<br>
<br>
#RDBMS<br>
1,RDBMS 即关系数据库管理系统(Relational Database Management System)的特点：<br>
1.数据以表格的形式出现<br>
2.每行为各种记录名称<br>
3.每列为记录名称所对应的数据域<br>
4.许多的行和列组成一张表单<br>
5.若干的表单组成database<br>
2, RDBMS的一些术语：<br>
数据库:数据库是一些关联表的集合。<br>
数据表:表是数据的矩阵。在一个数据库中的表看起来像一个简单的电子表格。<br>
列:一列(数据元素) 包含了相同类型的数据, 例如邮政编码的数据。<br>
行：一行（=元组，或记录）是一组相关的数据，例如一条用户订阅的数据。<br>
冗余：存储两倍数据，冗余降低了性能，但提高了数据的安全性。<br>
主键：主键是唯一的。一个数据表中只能包含一个主键。你可以使用主键来查询数据。<br>
外键：外键用于关联两个表。<br>
复合键：复合键（组合键）将多个列作为一个索引键，一般用于复合索引。<br>
索引：使用索引可快速访问数据库表中的特定信息。索引是对数据库表中一列或多列的值进行排序的一种结构。类似于书籍的目录。<br>
参照完整性: 参照的完整性要求关系中不允许引用不存在的实体。与实体完整性是关系模型必须满足的完整性约束条件，目的是保证数据的一致性。<br>
<br>
#下载MySQL<br>
1，根据教程下载MySQL数据库<br>
下载地址：https://dev.mysql.com/downloads/mysql/<br>
选择Microsoft Windows > Download > No thanks, just start my download.进行下载<br>
完成下载后解压到对应文件夹<br>
创建一个my.ini配置文件，具体方法为在C盘中搜索.ini后缀文件，（直接修改拓展名有奔溃风险）选择一个复制并粘贴到解压后文件夹内，修改文件名为my，编辑 my.ini 配置以下基本信息：<br>
[client]<br>
# 设置mysql客户端默认字符集<br>
default-character-set=utf8<br>
[mysqld]<br>
# 设置3306端口<br>
port = 3306<br>
# 设置mysql的安装目录<br>
basedir=C:\\web\\mysql-8.0.11<br>
# 设置 mysql数据库的数据的存放目录，MySQL 8+ 不需要以下配置，系统自己生成即可，否则有可能报错<br>
# datadir=C:\\web\\sqldata<br>
# 允许最大连接数<br>
max_connections=20<br>
# 服务端使用的字符集默认为8比特编码的latin1字符集<br>
character-set-server=utf8<br>
# 创建新表时将使用的默认存储引擎<br>
default-storage-engine=INNODB<br>
注：若在mysqld下行添加<br>
skip-grant-tables：跳过授权表，即无密码直接登陆，但要随用随关，重启mysql，否则服务器将面对风险。<br>
该命令也可能导致报错并导致mysql无法开启，若发生此现象注释掉该行命令即可<br>
<br>
 <br>
2，安装&启动MySQL<br>
①以管理员身份打开 cmd 命令行工具，切换目录到bin文件夹下（此处若不以管理员身份打开，则启动数据库报错“发送系统错误05，拒绝访问”）<br>
②初始化数据库 命令为mysqld --initialize --console<br>
③找到带有... A temporary password...的行，记录随机生成的初始密码<br>
 <br>
注：此密码也可通过在dota文件夹中找到以.err结尾的文件找到<br>
④输入安装命令mysqld install<br>
 <br>
⑤输入初始化data目录命令mysqld --initialize-insecure<br>
⑥输入启动命令net start mysq（因为配置的时候少打了一个l，所以我的数据库名为mysq）<br>
 <br>
3，登录MySQL<br>
 <br>
使用navicat成功连接<br>
 <br>
遇到的问题：<br>
②	进行初始化数据库前不应手动创建data文件夹，易使mysql数据库无法启动<br>
②进行环境变量配置后，即可在任意目录下登录mysql（路径：系统高级设置>环境变量>系统变量>path>新增bin目录）<br>
③	mysal8.0版本的密码修改命令：ALTER USER "root"@"localhost" IDENTIFIED  BY "新密码";<br>
④	连接Navicat时出现1251报错： <br>
解决方法见：https://www.cnblogs.com/blessYou/p/10766979.html；<br>
#MySQL的管理<br>
Windows下MySQL服务器的开关：<br>
开：net start mysql名（我是mysq）<br>
关：net start mysql名<br>
Mysql基本命令（增删改查）<br>
1.	创建/删除数据库 CREATE/drop DATABASE 数据库名<br>
 <br>
2.	创建数据表 CREATE TABLE table_name (column_name column_type);<br>
 <br>
数据类型：<br>
（网页截图）<br>
 <br>
注意：若设置字段属性 NOT NULL,操作数据库输入字段NULL则会报错<br>
插入数据：INSERT INTO table_name ( field1, field2,...fieldN ) VALUES( value1, value2,...valueN );<br>
 <br>
查询数据：SELECT column_name,column_name FROM table_name [WHERE Clause] [LIMIT N][ OFFSET M]<br>
<br>
<br>
查询使用多个表，表之间用逗号分割<br>
WHERE设定查询条件 <br>
*可代替其他字段，返回表的所有字段数据<br>
LIMIT设定返回记录数<br>
OFFSET指定SELECT语句开始查询的数据偏移量，默认情况下偏移量为0<br>
修改数据：UPDATE table_name SET 字段 1=值 1 [,字段 2=值 2… ] [WHERE ] [ORDER BY ] [LIMIT ]<br>
 <br>
SET ：用于指定表中要修改的列名及其列值。其中，每个指定的列值可以是表达式，也可以是该列对应的默认值。如果指定的是默认值，可用关键字 DEFAULT 表示列值。<br>
删除数据：DELETE FROM table_name  [WHERE ] [ORDER BY ] [LIMIT ]<br>
ORDER BY ：可选项。表示删除时，表中各行将按照子句中指定的顺序进行删除<br>
WHERE ：可选项。表示为删除操作限定删除条件，若省略该子句，则代表删除该表中的所有行。<br>
LIMIT ：可选项。用于告知服务器在控制命令被返回到客户端前被删除行的最大值。<br>
<br>