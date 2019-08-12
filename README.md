[TOC]
datax镜像

# 适用场景
适用于开发测试环境

# 功能
## 下载datax
## 解压datax
## 配置datax

## 下载jenkins
## 解压jenkins
## 配置jenkins


# 使用方式
```
# 构建
# docker build -t qq275860560/datax .
# 拉取
docker pull qq275860560/datax
# 运行
docker run -d -p 8081:8081 --name datax qq275860560/datax 
# 测试
curl localhost:8081 
```

# windows使用方式
```
#windows下载安装python27和datax
python d:/datax/bin/datax.py d:/datax/job/mysql-mysql.json
```

# 温馨提醒

* 此项目将会长期维护，增加或改进实用的功能
* 右上角点击star，给我继续前进的动力,谢谢