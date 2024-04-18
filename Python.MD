```python
# List按元素某个key的值排序
newlist = sorted(data, key=lambda x: x['value'], reverse=True)
```



#### 装饰器

本质是将函数作为参数输入，输出另一个函数

```python
# 装饰器
def decorator(func):
    def wrapper(*args, **kwargs):
        print("start")
        func(*args, **kwargs)
        print("end")
    return wrapper

@decorator
def f():
    print("function")

# 不用@语法
def f():
    print("function")
dec_f = decorator(f)

# 带参装饰器
def my_decorator(a, b):
    def decorator(func):
        def wrapper(*args, **kwargs):
            print(a)
            res = func(*args, **kwargs)
            print(b)
            return res
        return wrapper
    return decorator

@my_decorator("start", "end")
def f(x, y):
    return x*y

x = f(3, 4)
```



#### 多线程

```python
import threading, time

def worker(n):
    print("start")
    time.sleep(n)
    print("end")

threads = []
for _ in range(5):
    t = threading.Thread(target=worker, args=(2,))
    t.start()
    threads.append(t)
    
for t in threads:
    t.join()
print("finished")
```



#### 多进程

```python
import multiprocessing, time

def worker(n):
    print("start")
    time.sleep(n)
    print("end")

def main():
    processes = []
    for i in range(5):
        p = multiprocessing.Process(target=worker, args=(2, ))
        p.start()
        processes.append(p)
    
    for p in processes:
        p.join()

if __name__ == "__main__":
    main()
```



#### async

```python
```





#### 内置装饰器：@property

将函数转化为属性

```python
class Student(object):
    def __init__(self, name):
        self.name = name
        self._age = None

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if not isinstance(value, int):
            raise ValueError('输入不合法：年龄必须为数值!')
        if not 0 < value < 100:
            raise ValueError('输入不合法：年龄范围必须0-100')
        self._age=value

    @age.deleter
    def age(self):
        del self._age
```

#### @staticmethod 和 @classmethod

​		都可以通过类调用或者实例调用。

​		一个视作静态方法，不需要额外参数；一个是类方法，需要传入cls参数代替self表示类本身，因此可以通过cls.args的方式访问静态变量。

```python
# enumerate 
for index, value in enumerate(x):
    ...
```



# Flask

#### 特性

​		路由系统，插件系统，上下文管理，请求和响应对象，钩子函数，蓝图，Restful API，异步，部署（WSGI，uWSGI，Gunicorn），信号（Signals），WebSocket

#### 蓝图

用于项目模块化，一个蓝图即一组视图路由集合

```python
# 创建蓝图
from flask import Blueprint
bp = Blueprint('auth', __name__)

# 注册蓝图
from flask import Flask
app = Flask(__name__)
app.register_blueprint(bp, url_prefix='/auth')

# 定义视图函数
@bp.route('/login')
def login():
    return 'Login Page'
```

#### 上下文

​		应用上下文（Application Context）是整个 Flask 应用程序的上下文环境，它在应用程序启动时创建，并在应用程序关闭时销毁

​		请求上下文（Request Context）是在每个请求到达时创建的上下文环境，可以通过 `flask.request` 对象直接访问，并且在视图函数中默认是全局可用的。

​		测试上下文（Test Context）

#### 全局g变量

​		全局 `g` 变量是用于存储每个请求的全局变量的对象。它在同一个请求处理过程中是可用的，但对于不同的请求是隔离的。

#### 钩子函数

```python
# 请求处理之前的中间件
@app.before_request
def before_request():
    # 在这里可以执行一些逻辑，比如权限验证、日志记录等
    print('Before request:', request.url)

# 请求处理之后的中间件
@app.after_request
def after_request(response):
    # 在这里可以执行一些逻辑，比如设置响应头、处理异常等
    print('After request:', response.status)
    return response
```

#### 部署

```bash
gunicorn -b 0.0.0.0:8000 -w 4 -t 2 app:app
```

































