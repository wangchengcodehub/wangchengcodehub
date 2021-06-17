# Django中url与path及re_path区别

初学者一般不能分清两者的区别,所这简单介绍下两者.

首先,url是Django 1.x中的写法, 在Django2.1中，开始舍弃django1.x中的url写法。

在django2.x中，描写url配置的有两个函数path和re_path.re_path()函数可以看做是django 1.x中得url函数,即可以在路径中使用正则.



## 一.path和url的区别：

- django.urls path
- django.conf.urls url

path与url是两个不同的模块,效果都是响应返回页面, path调用的是python第三方模块或框架,而url则是自定义的模块,如Views下的def函数对应你url中的参数值.

例如:

```python
url(r'^login',views.login)，
def login(request):
    return render(request,'login.html')
```

### 1、url

在settings.py文件中有一个`ROOT_URLCONF`设置，设置的是在访问网址时通过哪一个url文件去匹配所请求的网址

#### url参数

url或者re_path要复杂一些 （`r’^blog/(?P[0-9]{4})/′）`首先需要开始符和结尾符 '） 首先需要开始符^和结尾符 ′）首先需要开始符和结尾符,参数匹配一个 （）就是一个匹配参数，
(?P<匹配的字段名>正则表达式)

进行匹配是不包括get或者post请求方式的参数及域名比如`www.qq.com/blog?num=1`并不会匹配？后边的字符

可以给request参数设置一个默认值,最常见的分页url，比如



```python
urlpatterns=[
    url(r'^page/$',views.page),
    url(r'^page(?P<num>[0-9]+)$',views.page)
]

#views

def page(request,num='1'):
    pass
```

自定义错误页面关键字handler400=blog.views.page_no_find



```bash
#urls.py
…
handler400=blog.views.page_no_find
```

### 2、path

参数的使用方法`path(‘blog/<str:string>/’)` 简单了很多，就是尖括号，前边是str代表参数的类型，后面代表参数的名称

#### path参数类型

捕获url中的参数需要用到尖括号<> 指定尖括号中的值类型比如int:astr:link这个转换器还有许多类型比如：

- int 匹配0和正整数
- str 匹配任何空字符串但不包括/
- slug 可理解为注释 匹配任何ascii码包括连接线和下划线
- uuid 匹配一个uuid对象（该对象必须包括破折号—，所有字母必须小写）
- path 匹配所有的字符串 包括/（意思就是path前边和后边的所有）

### 3.re_path

如果遇上路径和转换器语法都不足以定义的URL模式，那么就需要使用正则表达式，这时候就需要使用re_path()，而非path()。

举例：传递 数字结尾的参数



```python
re_path(r'(\d+)/$',views.peopleList,name='peopleList'),
```

## 二、python3中使用django2,常见设置path问题

### 1.Django2中使用

在python3中使用django2的时候，在设置urls的时候，会遇到一些坑。这里做一下记录。
系统的urls.py里，在1.X的时候，都是采用的url方式。如下



```python
url(r'^', include("test1.urls")),
```

在2.0中，它推荐使用的是path模块，所以这里就改写一下。引包



```jsx
from django.urls import path

path('', include("test1.urls")),
```

注意:

> 如果要使用正则，则要引入re_path，from django.urls import path, re_path
> 这里面的正则写法，有点意思，一定要使用（）把正则包起来，然后用?P正式表达式 这种形式来表式

### 2.APP中使用path

1.x里面的写法是



```ruby
url(r’^page=(\d+)&key=(\w+)$’, views.detail, name=”detail”),
```

现在的写法



```bash
re_path('page=(?P<page>\d+)&key=(?P<key>\w+)', views.detail, name="detail"),
```

这样一对比就能明白了吧,使用的链接是[http://127.0.0.1:8000/page=12&key=abc](https://links.jianshu.com/go?to=http%3A%2F%2F127.0.0.1%3A8000%2Fpage%3D12%26key%3Dabc)

### 3.系统的urls.py里的namespace的问题

1.x中写法



```python
url(r'^', include("test1.urls", namespace='test1')),
```

可是在2.0中你这么写，会报错，说什么app_name的，这个自己可以看一下，怎么解决呢，其实很简单，只要在自己项目urls.py中加上这句就行了.如果不加的话可能报错,



```bash
app_name = 'test1'(你的APP名)
```

注:

> ```ruby
> 使用url也是可以的,为了简便起见,尽量使用符合版本的字段,另外在写路径时应该严格按照语法,比如'^' 和/$就不能缺,不能前面写url,括号里面确按
> ```