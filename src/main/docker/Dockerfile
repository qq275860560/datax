FROM qq275860560/base

MAINTAINER jiangyuanlin@163.com

# install datax
RUN curl -fSL http://datax-opensource.oss-cn-hangzhou.aliyuncs.com/datax.tar.gz | tar xzf - -C /usr/local &&\
    echo 'export DATAX_HOME=/usr/local/datax/' >> /etc/profile && source /etc/profile &&\
    echo 'export PATH=$PATH:$DATAX_HOME/bin'   >> /etc/profile && source /etc/profile &&\
    chmod -R 755 /usr/local/datax
    
# 配置datax    
RUN mkdir -pv /usr/local/datax/plugin/reader/httpreader &&\
   cd /usr/local/datax/plugin/reader/httpreader && curl -fsSL -O "https://raw.githubusercontent.com/qq275860560/dataxweb/master/src/main/centos/usr/local/datax/plugin/reader/httpreader/httpreader-0.0.1-SNAPSHOT.jar" &&\
   cd /usr/local/datax/plugin/reader/httpreader && curl -fsSL -O "https://raw.githubusercontent.com/qq275860560/dataxweb/master/src/main/centos/usr/local/datax/plugin/reader/httpreader/plugin.json" &&\
   cd /usr/local/datax/plugin/reader/httpreader && curl -fsSL -O "https://raw.githubusercontent.com/qq275860560/dataxweb/master/src/main/centos/usr/local/datax/plugin/reader/httpreader/plugin_job_template.json" &&\
   /bin/cp -rf /usr/local/datax/plugin/reader/ftpreader/libs /usr/local/datax/plugin/reader/httpreader/
   	
RUN mkdir -pv /usr/local/datax/plugin/writer/httpwriter &&\
   cd /usr/local/datax/plugin/writer/httpwriter && curl -fsSL -O "https://raw.githubusercontent.com/qq275860560/dataxweb/master/src/main/centos/usr/local/datax/plugin/writer/httpwriter/httpwriter-0.0.1-SNAPSHOT.jar" &&\
   cd /usr/local/datax/plugin/writer/httpwriter && curl -fsSL -O "https://raw.githubusercontent.com/qq275860560/dataxweb/master/src/main/centos/usr/local/datax/plugin/writer/httpwriter/plugin.json" &&\
   cd /usr/local/datax/plugin/writer/httpwriter && curl -fsSL -O "https://raw.githubusercontent.com/qq275860560/dataxweb/master/src/main/centos/usr/local/datax/plugin/writer/httpwriter/plugin_job_template.json" &&\
   /bin/cp -rf  /usr/local/datax/plugin/writer/ftpwriter/libs /usr/local/datax/plugin/writer/httpwriter/ &&\
   cd /usr/local/datax/plugin/writer/httpwriter/libs && curl -fsSL -O https://repo1.maven.org/maven2/org/apache/httpcomponents/httpmime/4.5.9/httpmime-4.5.9.jar


# install jenkins
RUN wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo && \
    rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key && \
    yum info jenkins && yum -y  install  jenkins && yum -y update jenkins &&\
    yum -y clean all && rm -rf /var/cache/yum/*  /tmp/* /var/tmp/*

# init jenkins
RUN mkdir -pv /var/lib/jenkins/ && cd /var/lib/jenkins/ && curl  -O https://raw.githubusercontent.com/qq275860560/jenkins-master/master/src/main/centos/var/lib/jenkins/config.xml &&\
    cd /etc/sysconfig && curl -fsSL -O "https://raw.githubusercontent.com/qq275860560/dataxweb/master/src/main/centos/etc/sysconfig/jenkins"
 
CMD source /etc/profile &&\
    /usr/sbin/sshd &&\
    echo "run jenkins" &&\
    /etc/rc.d/init.d/jenkins start &&\
    tail -f /var/log/lastlog
   

 
