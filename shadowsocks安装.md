# 1.安装相关脚本,pip是 python 的包管理工具。在本文中将使用 python 版本的 shadowsocks，此版本的 shadowsocks 已发布到 pip 上，因此我们需要通过 pip 命令来安装.
  ```
  yun install python-setuptools && easy_install pip
  ```
# 2.安装shadowsocks
  ```
  pip install shadowsocks
  ```
# 3.配置shadowsocks服务
  ```
  vi /etc/shadowsocks.json
  ```
具体配置:
```
{
    "server":"my_server_ip",//服务器监听的地址
    "server_port":8388,//服务器端口
    "local_address": "127.0.0.1",//您当前的地址
    "local_port":1080,//本地港口
    "password":"mypassword",// 用于加密的密码
    "timeout":300,
    "method":"aes-256-cfb",//方法default: "aes-256-cfb",
    "fast_open": false
}
```
# 4.运行shadowsocks服务
  ```
  ssserver -c /etc/shadowsocks.json -d start
  ```
# 5.防火墙设置
  ```
  systemctl stop firewalld // 关闭防火墙
  systemctl disable firewallld // 禁用防火墙,防止服务器重启后自动打开防火墙
  systemctl status firewalld // 查看防火墙状态
  ```
# 6.测试
  telnet ip port
# 7.查看shadowsocks日志
  ```
  less /var/log/shadowsocks.log
  ```
