[TOC]
datax镜像

# 适用场景
适用于开发测试环境

# 功能
## 下载datax
## 解压datax
## 配置datax


# 使用方式
```
# 构建
# docker build -t qq275860560/datax .
# 拉取
docker pull qq275860560/datax
# 运行
docker run -it --name datax qq275860560/datax /bin/bash
# 测试
docker exec -it datax /bin/bash -c "source /etc/profile && cd /usr/local/datax/job/ && curl -O https://raw.githubusercontent.com/qq275860560/datax/master/src/main/centos/usr/local/datax/job/mysql-mysql.json"
docker exec -it datax /bin/bash -c "source /etc/profile && python /usr/local/datax/bin/datax.py /usr/local/datax/job/mysql-mysql.json"

docker exec -it datax /bin/bash -c "source /etc/profile && cd /tmp &&  git clone https://github.com/qq275860560/dataxweb.git “
docker exec -it datax /bin/bash -c "source /etc/profile && cd /tmp/dataxweb && mvn spring-boot:run "

```

# 温馨提醒

* 此项目将会长期维护，增加或改进实用的功能
* 右上角点击star，给我继续前进的动力,谢谢