# 2. REST基本特征

### 1.REST的最基本特征

我们把服务器提供的服务统一称为资源。
我们可以使用URL来定位资源，如/v1/book/user/1 来定位一个用户
定位到资源以后，可以使用HTPP动词来操作资源，类似使用DDL操作数据库。

![image.png](https://upload-images.jianshu.io/upload_images/7220971-3c2a7daa6f0cb9c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

对于视图函数的URL，尽量不应该包含动词，因为URL是用来定位资源的，例如我们之前的试图函数，应该这样改写
```python
@api.route('', methods=['GET'])
def get_book():
    return 'get book'


@api.route('', methods=['POST'])
def create():
    return 'create book'
```

### 2.为什么标准的REST不适合内部开发
REST的使用场景有两个：内部开发API，开放API。
标准的REST比较适合开放性的API

1. 由于内部的开发，业务逻辑非常复杂，想用简单的四个接口来标示所有的业务逻辑，基本上是不可能的
2. REST的接口粒度比较粗（返回的资源属性比较多；服务器不会负责处理数据），这样前端的开发是不太方便的
3. 标准的REST会造成HTTP请求的数量大幅度的增加