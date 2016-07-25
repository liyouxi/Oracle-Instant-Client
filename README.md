# Oracle-Instant-Client
## ubuntu 下安装 
要先安装alien工具，必须是在root下安装

`apt-get install alien`

### 1. 下载数据包文件 ###

`https://github.com/liyouxi/Oracle-Instant-Client.git`

`oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm`

`oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm`

`oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm`

### 2. 在sudo权限下将rpm文件转换成deb
`alien -k oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm`

`alien -k oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm`

`alien -k oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm`

### 3. Install deb package 或者双击安装也可
`dpkg -i oracle-instantclient12.1_basic-12.1.0.2.0-1.x86_64.deb`

`dpkg -i oracle-instantclient12.1_devel-12.1.0.2.0-1.x86_64.deb`

`dpkg -i oracle-instantclient12.1_sqlplus-12.1.0.2.0-1.x86_64.deb`

### 4.配置环境变量，需要在root权限下

`vim /etc/profile`


在文件最下面添加：

  `export ORACLE_HOME=/usr/lib/oracle/12.1/client`
  
  `export ORACLE_BASE=/usr/lib/oracle/12.1`
  
  `export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH`
  
  `export NLS_LANG=AMERICAN_AMERICA.AL32UTF8`
  
保存

  `source /etc/profile，启动配置`

  `reboot`

### 5.进入 /usr/lib/oracle/12.1/client/bin目录下 运行sqlplus。

## CentOS下安装 

1. 安装libaio和oracle client 

yum install libaio
rpm -Uvh oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm
rpm -Uvh oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm
rpm -Uvh oracle-instantclient12.1-sqlplus-12.1.0.2.0-1.x86_64.rpm

2. 添加  Oracle client 到  library path


echo "/usr/lib/oracle/12.1/client64/lib" >/etc/ld.so.conf.d/oracle.conf
ldconfig

3. install epel repo via yum extra


yum install epel-release

4. Install additional

yum install gcc python-pip.noarch python-devel
5. Install  cx_Oracle via pip

pip install cx_Oracle
