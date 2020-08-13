# 单个WebService container多个服务
# nginx-upstream
docker+nginx+node 负载均衡

docker network create compose_default
docker-compose up


# 测试
curl -I 127.0.0.1:4000　# 这个端口号是之前在yml文件中定义在nginx下面的ports里面的
多运行几次,然后打开nginx目录下的access.log文件,可以看到如下信息:

192.168.144.1 - -[13/Aug/2020:08:42:49 +0000] "curl/7.47.0" "-" "192.168.144.2:30001"
192.168.144.1 - -[13/Aug/2020:08:42:51 +0000] "curl/7.47.0" "-" "192.168.144.2:30000"

看最后一列的192.168.144.2:3000这样的地址,是我们具体容器的ip,每次请求nginx都会根据算法来调度,所以这些地址会变化,说明部署成功.
