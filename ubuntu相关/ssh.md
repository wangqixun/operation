# SSH
<br>

## 配置端口
```bash
sudo mkdir /run/sshd
sudo chown root:root -R /run/sshd
sudo chmod 644 -R /run/sshd
# 设置端口，这里以10022为例
sudo /usr/sbin/sshd -p 10022
```
设置密码认证权限
```bash
vi /etc/ssh/sshd_config
```
修改
```text
修改 PasswordAuthentication no -> yes
```
随后重启ssh```sudo service ssh start```


+ #### 重启
```
service ssh start
```



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


