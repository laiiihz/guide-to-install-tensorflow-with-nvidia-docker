# Arch系发行版安装指南
## 安装Nvidia显卡驱动
[安装Ubuntu18xx驱动](https://github.com/laiiihz/install_nvidia_driver_on_ubuntu_18_XX)
## Docker
### 安装Docker
```bash
sudo pacman -S docker  
```
### 测试Docker
```bash
docker run hello-world
```

> - [x] 在非sudo下运行docker，请创建 docker组并添加用户 
>* 若显示Unable to find image 'hello-world:latest' locally ,运行
> `docker pull hello-world`
>* 若显示Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running？请启动Docker服务,运行
> `sudo systemctl start docker`

显示`Hello from Docker!`则运行成功

### 运行 TensorFlow 容器(无GPU)
>* 下载容器
> ```bash
> docker pull tensorflow/tensorflow    
> ```
>* 启动一个Jupyter notebook服务
> ```
> docker run -it -p 8888:8888 tensorflow/tensorflow
> ```

### 安装Nvidia-docker v2
>* 使用yaourt等软件包安装AUR仓库中的Nvidia-docker v2
> `yaourt nvidia-docker`
>* 检查Nvidia显卡是否可用　｀lspci | grep -i nvidia｀
> 若不可用则检查显卡安装情况
### 验证 nvidia-docker 安装
```bash
docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi
```
* optirun启动　（需要安装Bumblebee）
```bash
optirun docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi
```
#### 结果如下
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 415.27       Driver Version: 415.27       CUDA Version: 10.0     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX XXXX    Off  | 00000000:01:00.0  On |                  N/A |
| N/A   26C    P0    N/A /  N/A |      9MiB /  2002MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
+-----------------------------------------------------------------------------+

```

### 使用最新的 TensorFlow GPU 映像在容器中启动 bash shell 会话
```bash
使用最新的 TensorFlow GPU 映像在容器中启动 bash shell 会话
```



## 参考
[TensorFlow](https://tensorflow.google.cn/install/docker)
