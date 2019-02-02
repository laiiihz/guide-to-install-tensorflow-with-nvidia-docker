# Arch系发行版安装指南
## 安装Nvidia显卡驱动

## 安装Docker
### Docker
```bash
sudo pacman -S docker  
```
### 测试Docker
```bash
docker run hello-world
```
>*  若显示Unable to find image 'hello-world:latest' locally ,运行
```bash
docker pull hello-world
```
>* 若显示Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running？请启动Docker服务
```bash
sudo systemctl start docker
```

