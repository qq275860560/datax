FROM qq275860560/base

MAINTAINER jiangyuanlin@163.com

# datax
RUN curl -fSL http://datax-opensource.oss-cn-hangzhou.aliyuncs.com/datax.tar.gz | tar xzf - -C /usr/local &&\
    echo 'export DATAX_HOME=/usr/local/datax/' >> /etc/profile && source /etc/profile &&\
    echo 'export PATH=$PATH:$DATAX_HOME/bin'   >> /etc/profile && source /etc/profile &&\
    chmod -R 755 /usr/local/datax

RUN cd /tmp/ && git clone https://github.com/alibaba/DataX.git &&\
    cd /tmp/DataX/otsstreamreader/ && curl -O https://raw.githubusercontent.com/qq275860560/datax/master/src/main/centos/tmp/DataX/otsstreamreader/pom.xml  &&\
    echo 'export DATAX_SRC_HOME=/tmp/DataX/'  >> /etc/profile && source /etc/profile

# maven
#RUN curl -fsSL http://archive.apache.org/dist/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz | tar xzf - -C /usr/local  &&\
#    mv /usr/local/apache-maven-3.3.9 /usr/local/maven &&\
#    echo 'export MAVER_HOME=/usr/local/maven/' >> /etc/profile && source /etc/profile &&\
#    echo 'export PATH=$PATH:$MAVER_HOME/bin'   >> /etc/profile && source /etc/profile
RUN wget http://repos.fedorapeople.org/repos/dchen/apache-maven/epel-apache-maven.repo -O /etc/yum.repos.d/epel-apache-maven.repo &&\
    yum -y install apache-maven
     
RUN cd /tmp/DataX && mvn install -DskipTests &&\
    echo 'export DATAX_HOME=/tmp/DataX/core/target/datax/' >> /etc/profile && source /etc/profile &&\
    echo 'export PATH=$PATH:$DATAX_HOME/bin'   >> /etc/profile && source /etc/profile &&\
    chmod -R 755 $DATAX_HOME

CMD source /etc/profile &&\
     service sshd start &&\
     service datax start 	

 
