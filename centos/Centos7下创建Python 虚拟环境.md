# Python 虚拟环境



#### 1.我们先创建一个隐藏目录 .virtualenvs，所有的虚拟环境都放在此目录下

```
1mkdir ~/.virtualenvs
```



#### 2.安装virtualenv

```
1pip3 install virtualenv
```



#### 3.安装virtualenvwrapper

```
pip3 install virtualenvwrapper
```

#### 4.配置.bashrc文件

`查找virtualenvwrapper.sh的位置`

```
1find / -name "virtualenvwrapper.sh"
```

`编辑~/.bashrc文件`

```
1vim ~/.bashrc 2 3export WORKON_HOME=$HOME/.virtualenvs 4export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3 5source /usr/local/bin/virtualenvwrapper.sh 
```

`渲染~/.bashrc`

```
1source ~/.bashrc 
```



#### 4.创建虚拟环境

```
1mkvirtualenv flaskenv 2which: no virtualenv in (/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin) 3ERROR: virtualenvwrapper could not find virtualenv in your path 
```

`出现上面的报错,解决方案：找到virtualenv的位置`

```
which virtualenvwrapper.sh 
```

`编辑~/.bashrc文件 修改为如下`

```

```

`渲染文件`

```
1source .bashrc 
```

`继续执行创建`

```

```

出现上面这种情况表示安装成功。



#### 5.虚拟环境中其他指令

```
1.退出虚拟环境: deactivate
2.切换虚拟环境: workon 虚拟环境名
3.删除虚拟环境: rmvirtualenv 虚拟环境名
```

