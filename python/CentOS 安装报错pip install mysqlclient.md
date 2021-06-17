# CentOS 安装报错pip install mysqlclient

```bash
ERROR: Complete output from command python setup.py egg_info:
    ERROR: /bin/sh: mysql_config: command not found
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-install-l2723ndl/mysqlclient/setup.py", line 16, in <module>
        metadata, options = get_config()
      File "/tmp/pip-install-l2723ndl/mysqlclient/setup_posix.py", line 51, in get_config
        libs = mysql_config("libs")
      File "/tmp/pip-install-l2723ndl/mysqlclient/setup_posix.py", line 29, in mysql_config
        raise EnvironmentError("%s not found" % (_mysql_config_path,))
    OSError: mysql_config not found
    ----------------------------------------
ERROR: Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-install-l2723ndl/mysqlclient/
```

解决办法：

```bash
yum install python3-devel
yum install mysql-devel
yum install gcc
```

