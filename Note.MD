## 资源 

#### 云主机

81.69.163.142

浅EDE2C3，深DECFA4

#### Ubuntu22.04换源

```bash
cp /etc/apt/sources.list /etc/apt/sources.list.bak
vi /etc/apt/sources.list

# 阿里源
deb http://mirrors.aliyun.com/ubuntu/ jammy main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-backports main restricted universe multiverse

# docker换源
docker cp /etc/apt/sources.list ub:/etc/apt/sources.list
```





## TODO

- docker容器通过名称互相访问，docker compose

- 系统初始化，创建数据表，初始数据

- 配置管理

- 日志外送

- 密码学

  

## Docker

```bash
# 自定义网络
docker network create local
docker network ls
docker network inspect local

# 启动app
docker run -d --network=local --name=app app

# 启动postgres
docker run -d -e POSTGRES_PASSWORD=123123 -e POSTGRES_DB=app --name=pgdb --network=local postgres

# 启动nginx
docker run -d -p 80:80 -p 443:443 --network=local --name=nginx mynginx

# 从Dockerfile创建
docker build -t xxx .

# 查看容器详情
docker inspect xxx
```





## Postgres

### psql

-  `psql -h localhost -p 5432 -U postgres -d app -W` 连接
-  `\?` #所有命令帮助
-  `\h` #sql命令帮助
-  `\l `#列出所有数据库&#x20;
-  `\d` #列出数据库中所有表&#x20;
-  `\dt` #列出数据库中所有表&#x20;
-  `\du` #显示所有用户
-  `\d [table_name]` #显示指定表的结构
-  `\c [database_name]` #切换到指定的数据库&#x20;
-  `\c` #显示当前数据库名称和用户
-  `\i testdb.sql` #执行sql文件
-  `\q` #退出连接

#### 创建数据库

```sql
CREATE DATABASE [name];
```







## 开发日志

#### 11.28

- 配置nginx代理转发服务端口成功，但使用docker内的nginx一直报502。
  - 认为问题在于docker里的localhost不是宿主机而是容器本身，所以访问不到其他docker里的服务。需要访问172开头的ip，了解到docker存在一个**docker0**的概念。
  - 网桥是什么？172开头的ip是什么？
  - 使用容器名访问的方式

#### 11.30

- 解决nginx docker代理的问题
  - 所有容器必须在同一个network中，可以直接用容器名访问
  - ping 容器名 curl 容器名
- docker最小系统无法操作
  - docker cp apt源进去 & apt update
  - 同步时间：apt install -y ntpdate && ntpdate ntp.ubuntu.com

#### 12.5

- vue有两个问题：页面跳转、发送请求

#### 12.7

- 看vue视频
- 跨域问题是后端解决的







