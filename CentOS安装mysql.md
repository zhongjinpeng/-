# 1.删除已安装的MySQL
## 1.1检查MariaDB
   ```
   rpm -qa|grep mariadb
   ```
## 1.2删除MariaDB(如果上述操作为空，跳过)
   ```
   rpm -e --nodeps mariadb-server
   rpm -e --nodeps mariadb
   rpm -e --nodeps mariadb-libs
   ```
## 1.3检查MySql
   ```
   rpm -qa|grep mysql
   ```
## 1.4删除MySql
# 2.下载MySql源,根据CentOS版本进行下载
  [官网地址](https://dev.mysql.com/downloads/repo/yum/)
  
  查看系统版本
  ```
  cat /etc/redhat-release
  ```
  下载
  ```
  wget 地址
  ```
# 3.安装MySql源
  ```
  sudo rpm -Uvh 文件名
  ```
  检查是否安装成功,相关资源是否有了
  ```
  yum repolist enabled | grep "mysql.*-community.*"
  ```
# 4.安装MySql
  ```
  sudo yum install mysql-community-server
  ```
# 5.相关命令(CentOS7)
  启动服务
  ```
  sudo systemctl start mysqld.service
  sudo service mysqld start(CentOS6)
  ```
  查看服务状态
  ```
  sudo systemctl status mysqld.service
  ```
  重启服务
  ```
  sudo systemctl restart mysqld.service
  ```
  暂停服务
  ```
  sudo systemctl stop mysqld.service
  ```
# 6.修改密码
   查看初始密码
   ```
   sudo grep 'temporary password' /var/log/mysqld.log
   ```
   ```
   mysql -uroot -p
   ```
   ```
   ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
   ```
# 7.远程连接
   ```
   create user '用户名'@'%' identified by  'password';
   grant all privileges on *.* to '用户名'@'%' with grant option;
   flush privileges;
   use mysql;
   SELECT User, Host FROM user;
   ```
   
  
