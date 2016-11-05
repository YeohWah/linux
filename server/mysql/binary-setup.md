# setup with a generic binary distribution


### 路径说明
- basedir=/app/mysql
- datadir=/app/mysql/data
- user = root
- group = root


### 不新建组和用户简单配置 
  ##### 准备
  shell>$ pwd  
  shell>: /app/  
  shell>$ ls  
  shell>: mysql-5.7.16-linux-glibc2.5-x86_64.tar.gz  
  shell>$ tar -zxvf mysql-5.7.16-linux-glibc2.5-x86_64.tar.gz  
  shell>$ mv mysql-5.7.16-linux-glibc2.5-x86_64 mysql  
  shell>$ cd mysql  
  shell>$ pwd  
  shell>: /app/mysql/  
  shell>$ mkdir data  
  shell>$ ls  
  shell>: bin/  COPYING  docs/  include/  lib/  man/  README  share/  support-files/  data/  
  
  ##### 开始配置
  
  shell>$ bin/mysqld --initialize --user=root --basedir=/app/mysql --datadir=/app/mysql/data  
  shell>: ...  
  shell>: [Note] A temporary password is generated for root@localhost: p17p>qrr5Msp  
  此处需要注意记录生成的临时密码，如上文：p17p>qrr5Msp    
  
  shell>$ bin/mysql_ssl_rsa_setup  --datadir=/app/mysql/data  
  shell>: ...  
  可以忽略  
  
  shell>$ bin/mysqld_safe --user=root &  
  shell>: 2016-10-26T09:02:49.502483Z mysqld_safe Starting mysqld daemon with databases from /app/mysql/data  
  shell>$ ps -ef | grep mysql  
  
  ###### 启动完成，然后登陆修改root密码  
  
  shell>$ bin/mysql -uroot -p  
  Enter password: p17p>qrr5Msp  
  
  mysql> set password=password('permit');  
  mysql> show databases;  
  完成  
  
  ###### 其他 
  添加系统路径  
  shell>$ vim /etc/profile  
  添加：  
  export PATH=/app/mysql/bin:$PATH  
 
  shell>$ source /etc/profile  
  
  ##### 开机启动
  shell>$ cp /app/mysql/support-files/my-default.cnf /etc/my.cnf
  shell>$ vim /etc/my.cnf
  -------------------------------
         my.cnf
  
  shell>$ cp /app/mysql/support-files/mysql.server /etc/init.d/mysqld
  shell>$ vim /etc/init.d/mysqld
  --------------------------------
          user=root
          basedir=/app/mysql
          datadir=/app/mysql/data
  --------------------------------
  
  finished
  
  ##### ref
    http://www.jb51.net/article/87160.htm
    http://dev.mysql.com/doc/refman/8.0/en/binary-installation.html
  
  
    
