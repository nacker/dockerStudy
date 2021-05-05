#Docker环境的搭建

# 1.安装Mysql

```shell
docker run --name mysql -p 3307:3306 -e MYSQL_ROOT_PASSWORD=Abc1234?? -d mysql:5.7 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```

#2.Redis安装

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

# 3.安装MongoDB

```
docker run --name mongo -p 27017:27017 -d mongo --auth
```

```
docker -exec -it mongo mongo admin
db.createUser({ user:'admin',pwd:'123456',roles:[ { role:'userAdminAnyDatabase', db: 'admin'}]});
```

# 4.Nacos-Server

```
docker run --name nacos -e MODE=standalone -p 8848:8848 -d nacos/nacos-server:1.1.4
```

# 5.Sentinel-Dashboard

```
docker run --name sentinel  -p 8858:8858 -d  bladex/sentinel-dashboard
```

```
http://127.0.0.1:8858/
sentinel
sentinel
```