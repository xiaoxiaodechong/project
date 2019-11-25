### ①.搭建项目idea

1.下载项目

2.在idea 新建项目，搭建好环境，比如jdk 和Tomcat的包，把包引入（注意导入jdk不然会出问题）。

3.把项目文件中的src文件的文件替换到idea新项目的src中全部替换，把webcontent（其他项目不一定是这个名字）替换idea项目的web文件（遇到的问题，没有吧idea项目本身自带的文件给全部替换掉导致访问不到）

4.选择右上方的eidt_configuration选择配置Tomcat ，

5.点击加号选择Tomcat server

6.选择本地local 

7.选择server ，选择application server 选择Tomcat jar包

8.选择jer , 选择jar包

9.设置端口号

10.选择deployment ，在server旁边 ，切换后，点击右边加号，选择Artifact

11.在application中出现项目名称，也就是项目中out文件中的artifact文件下的项目名称，该项目名称部署到linux系统中，安装了Tomcat下的文件中的webapps下的项目名称



12.需要配置文件，该项中文件时hibernate.cfg.xml ，设置相关数据

#### ②数据库安装总结

解压包安装数据库

步骤：

1.解压文件

2.设置环境变量、设置到bin目录下

3.新建一个my.ini配置文件

设置情况如下：

[mysqld]
basedir=D:\mysql\mysql-5.7.25-winx64\mysql-5.7.25-winx64
datadir=D:\mysql\mysql-5.7.25-winx64\mysql-5.7.25-winx64\data
port=3306
skip-grant-tables
character-set-server=utf8  

#创建新表时将使用的默认存储引擎  

default-storage-engine=INNODB
sql_mode=NO_ENGINE_SUBSTITUTION,NO_AUTO_CREATE_USER

4.在win7的dos窗口下输入mysqld   --install  注意在bin目录下

5.在bin文件下初始化文件`mysqld --initialize-insecure --user=mysql;`

6.登入 mysql -u root

7.遇到问题：没有数据库中没有mysql文件  解决办法，没有初始化文件

8.服务器net start mysql 启动不了：删除data文件，从新初始化文件



### ③linux环境搭建总结

1.在网站下载linux tomcat包，解压到需要的文件当中，配置端口号等相关文件conf目录下的server中

2.把idea中out文件下生成的文件放置在webapps下，访问路径：http:// ip地址：端口号/项目名字

3.搭建环境：安装jar包，有三种安装方式，用yum 安装方式 命令：yum  install  -y   包名。用命令：yum  list java* 查看安装jdk包的名字

4.配置环境变量：/etc/profile 文件末尾下

配置环境如下：

#set java environment
JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk.x86_64
JRE_HOME=$JAVA_HOME/jre
CLASS_PATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar:$JRE_HOME/lib
PATH=$PATH:$JAVA_HOME/bin:$JRE_HOME/bin
export JAVA_HOME JRE_HOME CLASS_PATH PATH

遇到问题：本地无法通过ip地址访问linux Tomcat服务器、

解决办法：
