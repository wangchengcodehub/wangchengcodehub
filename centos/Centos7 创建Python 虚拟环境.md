# Python 虚拟环境



#### 1.创建一个隐藏目录 .virtualenvs，所有的虚拟环境都放在此目录下

```bash
mkdir ~/.virtualenvs
```

#### 2.安装 pip3

```bash
yum install python3-pip 
```

#### 3.安装virtualenv

```bash
pip3 install virtualenv
```

#### 4.安装virtualenvwrapper

```bash
pip3 install virtualenvwrapper
```

#### 5.配置.bashrc文件

`查找virtualenvwrapper.sh的位置`

```bash
which virtualenvwrapper.sh
```

> 编辑`~/.bashrc`文件

```bash
vim ~/.bashrc 

export WORKON_HOME=$HOME/.virtualenvs 
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3 
source /usr/local/bin/virtualenvwrapper.sh 
```

`渲染~/.bashrc`

```bash
source ~/.bashrc 
```

#### 6.创建虚拟环境

```
mkvirtualenv msb_py3 -p python3
```

`渲染文件`

```
1source .bashrc 
```

> 出现上面这种情况表示安装成功。

#### 7.虚拟环境中其他指令

```
1.退出虚拟环境: deactivate
2.切换虚拟环境: workon 虚拟环境名
3.删除虚拟环境: rmvirtualenv 虚拟环境名
```

