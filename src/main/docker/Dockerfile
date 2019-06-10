FROM qq275860560/base

MAINTAINER jiangyuanlin@163.com

# datax
RUN curl -fsSL http://datax-opensource.oss-cn-hangzhou.aliyuncs.com/datax.tar.gz | tar xzf - -C /usr/local  &&\
    mv /usr/local/datax /usr/local/datax &&\
    echo 'export DATAX_HOME=/usr/local/datax/' >> /etc/profile && source /etc/profile &&\
    echo 'export PATH=$PATH:$DATAX_HOME/bin'   >> /etc/profile && source /etc/profile


CMD source /etc/profile &&\
     service sshd start &&\
     service datax start 	

 
