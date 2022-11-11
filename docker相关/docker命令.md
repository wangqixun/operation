# docker命令
<br>

## 容器
+ #### 生成与启动
```
nvidia-docker run -ti --shm-size=16g --name=ygw-ml -p 7018:8888 -p 2011:22 -p 6001:6006 -v /data/gago_yangguowei/docker:/workspace -w /workspace ygw:v1 bash

docker start/stop ygw-tf
```
+ #### 解决中文编码问题
+ + 临时
```
docker exec -ti -e LANG=C.UTF-8 ygw-tf-nas bash
```
或进入容器后，在终端里执行
```
export LANG=C.UTF-8
```

## 容器迁移三部曲
```
docker commit 8495465a155a ygw:tf   # 从 container 8495465a155a  生成镜像 ygw:tf     ### docker commit --help
docker save -o ./ygw-tf.tar ygw:tf    # 打包镜像 ygw:tf 到文件 ./ygw-tf.tar       ### docker save --help
docker load -i ./ygw-tf.tar    # 从 ygw-tf.tar 文件中加载生成镜像        ### docker load --help
```

## push三部曲
```
docker login
docker commit 8495465a155a 18611684528/tf13_gpu-py3   # 从 container 8495465a155a 生成镜像 18611684528/tf13_gpu-py3
docker push 18611684528/tf13_gpu-py3
```

## 删除
+ #### 删除容器
```
docker rm 容器名字
```
+ #### 删除镜像
```
docker rmi $(docker images --quiet --filter "dangling=true")
```





