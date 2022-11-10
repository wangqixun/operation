### 1、重启系统
### 2、选择：ubuntu高级选项，按enter键
### 3、选择：xxxxxxxxx（recovery mode），按e键
### 4、Control + X
### 5、选择：root Drop to root shell prompt , 按enter键
### 6、按enter键进入终端，root权限
### 7、passwd user，修改user密码
### 8、passwd，修改root密码
#### 
#### 若出现：passwd：passwd unchanged
#### 则输入：mount -o rw,remount /.（注意‘/’前有空格，‘.’前面没空格）
### 9、修改完毕后，reboot重启