# Oracle-Instant-Client
要先安装alien工具，必须是在root下安装

`apt-get install alien`

### 1. 下载数据包文件 ###

`https://github.com/liyouxi/Oracle-Instant-Client.git`

`oracle-instantclient11.1-basic-11.1.0.7.0-1.i386.rpm`

`oracle-instantclient11.1-devel-11.1.0.7.0-1.i386.rpm`

`oracle-instantclient11.1-sqlplus-11.1.0.7.0-1.i386.rpm`

### 2. 将rpm文件转换成deb
`alien -k Oracle-instantclient11.1-basic-11.1.0.7.0-1.i386.rpm`
`alien -k Oracle-instantclient11.1-devel-11.1.0.7.0-1.i386.rpm`
`alien -k Oracle-instantclient11.1-sqlplus-11.1.0.7.0-1.i386.rpm`

### 3. Install deb package 或者双击安装也可
`dpkg -i oracle-instantclient11.1-basic_11.1.0.7.0-1_i386.deb`
`dpkg -i oracle-instantclient11.1-devel_11.1.0.7.0-1_i386.deb`
`dpkg -i oracle-instantclient11.1-sqlplus_11.1.0.7.0-1_i386.deb`

### 4.配置环境变量，需要在root权限下

`vim /etc/profile`

注意：如果要提示删除交换文件，就删除吧，要不然运行sqlplus会出现一堆鸟问题，反正我是遇到了啊。

在文件最下面添加：

  export ORACLE_HOME=/usr/lib/oracle/11.2/client
  export ORACLE_BASE=/usr/lib/oracle/11.2
  export LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH
  export NLS_LANG=AMERICAN_AMERICA.AL32UTF8
保存

  source /etc/profile，启动配置

  reboot

### 5.进入 /usr/lib/oracle/11.2/client/bin目录下 运行sqlplus。
