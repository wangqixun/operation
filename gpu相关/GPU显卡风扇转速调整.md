# GPU显卡风扇转速调整
<br>

1. #### 装好驱动

2. #### 配置
```
sudo vi ~/edid.txt
```
写入
```
00 ff ff ff ff ff ff 00 1e 6d f5 56 71 ca 04 00 05 14 01 03 80 35 1e 78 0a ae c5 a2 57 4a 9c 25 12 50 54 21 08 00 b3 00 81 80 81 40 01 01 01 01 01 01 01 01 01 01 1a 36 80 a0 70 38 1f 40 30 20 35 00 13 2b 21 00 00 1a 02 3a 80 18 71 38 2d 40 58 2c 45 00 13 2b 21 00 00 1e 00 00 00 fd 00 38 3d 1e 53 0f 00 0a 20 20 20 20 20 20 00 00 00 fc 00 57 32 34 35 33 0a 20 20 20 20 20 20 20 01 3d 02 03 21 f1 4e 90 04 03 01 14 12 05 1f 10 13 00 00 00 00 23 09 07 07 83 01 00 00 65 03 0c 00 10 00 02 3a 80 18 71 38 2d 40 58 2c 45 00 13 2b 21 00 00 1e 01 1d 80 18 71 1c 16 20 58 2c 25 00 13 2b 21 00 00 9e 01 1d 00 72 51 d0 1e 20 6e 28 55 00 13 2b 21 00 00 1e 8c 0a d0 8a 20 e0 2d 10 10 3e 96 00 13 2b 21 00 00 18 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 26
```
```
sudo nvidia-xconfig -a --allow-empty-initial-configuration --use-display-device="DFP-0" --connected-monitor="DFP-0" --custom-edid="DFP-0:/home/$USER/edid.txt"  --cool-bits=28
```
重启
```
sudo reboot
```

4. #### 触发
```
其中 GPUID = 0、1、2、3 ...，最后的 1 表示True
sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [gpu:GPUID]/GPUFanControlState=1

其中 GPUID = 0、1、2、3 ...，
sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [fan:GPUID]/GPUTargetFanSpeed=100


# 2卡4风扇
sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [gpu:0]/GPUFanControlState=1
sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [gpu:1]/GPUFanControlState=1

sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [fan:0]/GPUTargetFanSpeed=100
sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [fan:1]/GPUTargetFanSpeed=100
sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [fan:2]/GPUTargetFanSpeed=100
sudo DISPLAY=:0 XAUTHORITY=/var/run/lightdm/root/:0 nvidia-settings -c :0 -a [fan:3]/GPUTargetFanSpeed=100
```
