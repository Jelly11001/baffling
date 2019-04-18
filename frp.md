# frp的配置
[frp](https://github.com/fatedier/frp) 是一款反向代理软件，相对于[ngrok](https://ngrok.com/) 配置更简单
## 服务端
```
[common]
bind_port = 7000           #与客户端绑定的进行通信的端口
vhost_http_port = 6081     #访问客户端web服务自定义的端口号
```
## 客户端
```

[common]
server_addr = 120.56.37.48   #公网服务器ip
server_port = 7000            #与服务端bind_port一致
 
#公网通过ssh访问内部服务器
[ssh]
type = tcp              #连接协议
local_ip = 192.168.3.48 #内网服务器ip
local_port = 22         #ssh默认端口号
remote_port = 6000      #自定义的访问内部ssh端口号
 
#公网访问内部web服务器以http方式
[web]
type = http         #访问协议
local_port = 8081   #内网web服务的端口号
custom_domains = repo.iwi.com   #所绑定的公网服务器域名，一级、二级域名都可以
--------------------- 
```
## 开机自启
