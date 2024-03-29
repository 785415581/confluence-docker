如何使用
===

- 安装 docker
```bash
  yum install docker -y
```

- 安装 docker-compose
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

- 检查 docker-compose
```bash
docker-compose --version
# docker-compose version 1.24.0, build 1110ad01
```

- 自己创建或者下载本仓库里的docke-compose.yml

- 运行镜像服务
```bash
docker-compose up -d
```

- 浏览器访问服务器地址8090 端口(以下需要换成你的电脑的ip地址)，完成后续安装
```bash
http://192.168.1.173:8090
```

- 创建数据库
```bash
docker exec -it postgres96 /bin/bash
# 进入数据库容器 （postgre96 是数据库容器名称或者id ）

su - postgres
# 切换到数据库服务账户

psql
# 进入数据库命令行

CREATE USER confluence_db_user;
# 创建数据库用户

CREATE DATABASE confluence_db;
# 创建数据库

GRANT ALL PRIVILEGES ON DATABASE confluence_db TO confluence_db_user;
# 赋予用户权限

\password confluence_db_user;
# 密码
# 确认密码

\q
# 退出数据库命令行

exit
# 退出数据库服务账户

exit
# 退出登录容器
```
- 数据库设置
```
地址：postgres96（就是yml里第一个service的名字）
端口：5432
数据库：confluence_db
用户：confluence_db_user
密码：（confluence_db_user 密码）
```

- 停止与重启
```bash
docker-compose stop
docker-compose stop postgres96
docker-compose stop confluence

docker-compose start
docker-compose start postgres96
docker-compose start confluence
```
