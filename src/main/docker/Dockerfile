FROM qq275860560/base

MAINTAINER jiangyuanlin@163.com

# datax
RUN curl -fSL http://datax-opensource.oss-cn-hangzhou.aliyuncs.com/datax.tar.gz | tar xzf - -C /usr/local &&\
    echo 'export DATAX_HOME=/usr/local/datax/' >> /etc/profile && source /etc/profile &&\
    echo 'export PATH=$PATH:$DATAX_HOME/bin'   >> /etc/profile && source /etc/profile &&\
    chmod -R 755 /usr/local/datax

RUN cd /tmp/ && git clone https://github.com/alibaba/DataX.git &&\
    cd /tmp/datax/src/main/centos/tmp/DataX/otsstreamreader/ && curl -O https://raw.githubusercontent.com/qq275860560/datax/master/src/main/centos/tmp/DataX/otsstreamreader/pom.xml  &&\
    echo 'export DATAX_SRC_HOME=/tmp/DataX/' 
     


    
CMD source /etc/profile &&\
     service sshd start &&\
     service datax start 	

 
