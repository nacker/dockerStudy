#Docker环境的搭建

# 1.Docker环境安装
```
安装yum-utils
yum install -y yum-utils device-mapper-persistent-data lvm2
为yum源添加docker仓库位置：
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
安装docker：
yum install docker-ce
启动docker：
systemctl start docker
```

# 2.Nginx安装
```
docker pull nginx:1.10

docker run -d -p 8080:80 -v /data/nginx.conf:/etc/nginx/nginx.conf nginx:1.10
```

# 3.安装Mysql

```shell
docker run --name mysql -p 3307:3306 -e MYSQL_ROOT_PASSWORD=Abc1234?? -d mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

#4.Redis安装

```
docker run --name redis -p 6380:6379 -d redis
```

```
# 进入redis容器里面
docker exec -it redis bash
# 切换目录
cd /usr/local/bin
# 配置密码
./redis-cli
CONFIG SET requirepass Abc1234??
```

# 5.安装MongoDB

```
docker run --name mongo -p 27017:27017 -d mongo --auth
```

```
docker -exec -it mongo mongo admin
db.createUser({ user:'admin',pwd:'123456',roles:[ { role:'userAdminAnyDatabase', db: 'admin'}]});
```

# 6.Nacos-Server

```
docker run --name nacos -e MODE=standalone -p 8848:8848 -d nacos/nacos-server:1.1.4
```

# 7.Sentinel-Dashboard

```
docker run --name sentinel  -p 8858:8858 -d  bladex/sentinel-dashboard
```

```
http://127.0.0.1:8858/
sentinel
sentinel
```
# 8.gogs
```
docker pull gogs/gogs
mkdir -p /var/gogs
docker run --name=gogs -d  -p 10022:22 -p 10080:3000 -v /var/gogs:/data gogs/gogs

mac
docker run -d -p 10022:22 -p 10088:3000 --name=gogs --net=backend -v /var/gogs/:/data gogs/gogs
```

```
参数说明:
-d: 后台方式运行容器
-p: 端口映射, 将容器的22端口映射到宿主机的10022端口, 将容器的3000端口映射到宿主机的10080端口
–name: 指定容器名称
-v: 数据卷挂载, 用于将容器和数据分离

http://宿主机ip:10080
如: http://localhost:10080
```

