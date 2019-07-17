
# 概述

    安装基于独立mysql的hive

# 环境
    
    centos7
    mysql5.7
    hadoop2.6.5
    hive1.2.2

# 准备mysql

    启动mysql
    开启远程访问
        grant all privileges on *.* to 'root'@'%' identified by '123456';  

# 准备hadoop

    启动hadoop
    创建目录
        hadoop fs -mkdir -p /hive/warehouse

# 安装Hive

下载

    http://www.apache.org/dyn/closer.cgi/hive/
    换个镜像
   
安装

     tar -xzvf hive-x.y.z.tar.gz -C /opt

配置PATH
    
    vi /etc/profile
    export HIVE_HOME=/opt/hive-1.2.2
    export PATH=$HIVE_HOME/bin:$PATH
    . /etc/profile
    
测试

    hive --version

# hive-site.xml    

设置

    cd /usr/local/apache-hive-1.2.2/conf
    cp hive-default.xml.template hive-site.xml
    vim hive-site.xml
        删除里面内容，只留<configuration></configuration> 节点
        将光标放在<configuration>的下一行在:模式下输入.,$-1d 按回车 

内容

    <property>
        <name>hive.metastore.warehouse.dir</name>
        <value>/hive/warehouse</value>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionURL</name>
        <value>jdbc:mysql://msi:3306/hive?createDatabaseIfNotExist=true</value>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionDriverName</name>
        <value>com.mysql.jdbc.Driver</value>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionUserName</name>
        <value>root</value>
    </property>
    <property>
        <name>javax.jdo.option.ConnectionPassword</name>
        <value>Admin123!</value>
    </property>


# mysql 驱动

下载

    https://dev.mysql.com/downloads/connector/j/
    选择platform independent

设置
    
    解压得到jar包
    放到hive的lib目录下

# 更新jline.jar 

    在早期Hadoop版本中 jline.jar的版本是0.9+ 使用这个版本会报错，所以要替换成新版本的Jar包；
    
下载
    
    http://maven.outofmemory.cn/jline/jline/2.12.1/
更新
 
    cd /usr/local/hadoop-2.6.5/share/hadoop/yarn/lib
    rm -rf  jline-0.9.94.jar
    cp /root/jline-2.12.1.jar ./


# 启动
   
    hive

# 问题

mysql The server time zone value 'EDT' is unrecognized 

    https://blog.csdn.net/u014662563/article/details/61923884

Cannot find hadoop installation: $HADOOP_HOME or $HADOOP

    cp hive-env.sh.template hive-env.sh
    sudo vim hive-env.sh
    (加入export HADOOP_HOME=/usr/local/hadoop)
    source hive-env.sh
    
# 参考

    https://www.cnblogs.com/raphael5200/p/5175973.html
