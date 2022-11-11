## 僵尸程序
+ 杀死含有“关键字”的程序
```
kill -9 $(ps ax | grep "关键字" | fgrep -v grep | awk '{ print $1 }')
```
+ 清除僵尸进程Zombie
```
ps -A -ostat,ppid,pid,cmd | grep -e '^[zZ]' 
kill -HUP ppid
```

## 逐行分析python耗时
1. 安装

终端下执行
```
pip install line-profiler
```
2. 标记修饰器

在需要分析性能的函数前面加上修饰器“@profile”
```python
@profile
def func():
    pass

```
3. 分析

终端下执行
```
kernprof -l xxxx.py
```

## 命令行下虚拟屏幕(3DP为例)
终端下执行
```
#!/bin/sh
Xvfb :0 -screen 0 1024x768x24 -ac +extension GLX +render -noreset &
export DISPLAY=:0.0
python -c "import vispy; print(vispy.sys_info())"

# 运行
python main.py --config argument.yml
```

## youtube-dl下载
[更多资料](https://cloud.tencent.com/developer/article/1510301)
```python
import sys
cmd = "youtube-dl --proxy http://oversea-squid5.sgp.txyun:11080 --max-filesize 500m --write-info-json --playlist-end 10 --min-views 10000 --dateafter now-2000days --max-downloads 10 -i -f 'bestvideo[height<=720]+bestaudio[height<=720]/best[ext=mp4]/best' -o '%s' '%s'" % (target_dir, channel_url)
sys.system(cmd)
```





# 挂载硬盘
    sudo fdisk -l
    sudo mkfs -t ext4 /dev/sdb
    sudo mount /dev/sdb /data
    
    sudo apt-get install ntfs-3g       #对于ntfs的支持
    sudo apt-get install exfat-utils   #对于exfat的支持

    



# scp
    scp source dest

    scp -r ./model_weights/ gago_yangguowei@192.168.100.189:~/code/model_weights/




# NAS 
# mount/umount nas
    mount -t cifs //192.168.100.194/yangguowei /data/gago_yangguowei/docker/nas  -o vers=2.0,username=yangguowei,password=ygw@@123,dir_mode=0700,file_mode=0700,uid=gago_yangguowei,gid=gago_yangguowei,sec=ntlmssp
    
    umount /data/gago_yangguowei/docker/nas  或者 umount //192.168.100.194/yangguowei		
    mount.cifs  //192.168.100.194/yangguowei /data/gago_yangguowei/docker/nas/ -o user=yangguowei

# Conda

    conda info 查看conda 配置信息
    
## conda 源更换

    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
    conda config --set show_channel_urls yes



# pip
## pip 源更换
    修改或创建
    ~/.pip/pip.conf 

    添加
    [global]
    index-url = https://pypi.tuna.tsinghua.edu.cn/simple




# 英伟达驱动
## 下载
https://www.nvidia.cn/Download/index.aspx?lang=cn#
## 安装
sudo service lightdm stop

sudo bash ./NVIDIA-Linux-x86_64-384.130.run

sudo service lightdm start

