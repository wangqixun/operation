# SSH
<br>

+ #### 代号+免密登陆
```
vi .ssh/config
```
添加以下相关信息
```
# 添加需要连接的远程机器
Host sage
 hostname sage.sagenaoc.science
 port 22
 user wangqixun
 IdentityFile ~/.ssh/id_rsa
```
本地执行
```
ssh-copy-id sage
```
以后每次连
```
ssh sage
```


+ #### 自动断线解决
```
ssh -o ServerAliveInterval=30 wangqixun@sagenaoc.sagenaoc.science
```



+ #### 端口映射
```
# 远程8888 -> 本地8008
ssh -p 7969 gago_yangguowei@192.168.100.242 -L 8008:localhost:8888
```


