# ubuntu安装ssh以及开启root用户ssh登录

## 一、安装ssh

```bash
#切到root下面安装
sudo -i
sudo apt update
sudo apt install openssh-server
sudo service ssh start
ps -aux | grep ssh  # 检查是否启动成功 
```

## 二、开启root用户ssh登录

```bash
1.输入root账户的用户名密码切换到root目录： 
su

2.修改sshd配置文件: 
vi /etc/ssh/sshd_config

3.找到相关配置：
PermitRootLogin prohibit-password

4.更改为：
PermitRootLogin yes

5. 重启sshd
systemctl restart sshd

6.尝试ssh登录即可
```