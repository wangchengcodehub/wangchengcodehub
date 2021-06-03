# 教你如何在 CentOS 7 下 yum 方式安装 Docker 环境

**1、移除旧版本：**

```
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine
rm -rf /etc/systemd/system/docker.service.d
rm -rf /var/lib/docker
rm -rf /var/run/docker
rm -rf /usr/local/docker
rm -rf /etc/docker
```

**2、安装一些必要的系统工具：**

```
yum -y install yum-utils device-mapper-persistent-data lvm2
```

**3、添加软件源信息：**

```
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

**4、更新 yum 缓存：**

```
yum makecache fast
```

**5、安装 Docker-ce：**

```
yum -y install docker-ce
```

**6、启动 Docker 后台服务：**

```
systemctl start docker
```

**7、测试运行 hello-world：**

```
docker run hello-world
```

**8、安装centos，并以后台启动的方式运行centos：**

```
docker run -itd centos /bin/bash
```

**9、进入centos镜像：**

```
[root@myserver ~]# docker ps
CONTAINER ID        IMAGE              COMMAND            CREATED              STATUS              PORTS              NAMES
f57d4703adc3        centos              "/bin/bash"        About a minute ago  Up About a minute                      jolly_dhawan
[root@myserver ~]# docker exec -it f57d4703adc3 /bin/bash
[root@f57d4703adc3 /]#
[root@f57d4703adc3 /]# cat /etc/RedHat-release 
CentOS Linux release 7.6.1810 (Core) 
[root@f57d4703adc3 /]#
```

至此，Docker环境搭建完成。