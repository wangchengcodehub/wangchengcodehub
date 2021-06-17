# PIPY依赖管理工具【HUAWEI】

新手指引

`准备工作`

> 使用前请确保您已安装python和[pip](https://pip.pypa.io/en/stable/installing/)，如果您尚未安装python，可以点击下面链接加速下载安装：

```bash
Python加速地址：https://repo.huaweicloud.com/python/
```



`临时使用`

> 运行以下命令使用华为开发云软件源安装软件包：

```bash
pip install --trusted-host https://repo.huaweicloud.com -i https://repo.huaweicloud.com/repository/pypi/simple
```

`设为默认`

> Pip的配置文件为用户根目录下的：`~/.pip/pip.conf`（Windows路径为：`C:\Users\<UserName>\pip\pip.ini`）, 您可以配置如下内容：

```bash
[global]
index-url = https://repo.huaweicloud.com/repository/pypi/simple
trusted-host = repo.huaweicloud.com
timeout = 120
```



`相关网址`

> Python官方地址：https://www.python.org/

> Pypi文档地址：[https://pypi.org](https://pypi.org/)

