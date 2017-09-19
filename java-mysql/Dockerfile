FROM mysql/mysql-server:5.7
MAINTAINER bassy-wmoon
WORKDIR /root

# Configure MySQL
COPY conf/my.cnf /etc/my.cnf
ENV MYSQL_ALLOW_EMPTY_PASSWORD yes
ENV MYSQL_ROOT_HOST 172.17.0.1

# Enviroment variables
ENV LANG=C

# Install software 
RUN yum -y install tar wget git

# Install JDK8
RUN wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u144-b01/090f390dda5b47b9b721c7dfaa008135/jdk-8u144-linux-x64.rpm
RUN yum -y localinstall jdk-8u144-linux-x64.rpm
RUN rm jdk-8u144-linux-x64.rpm
ENV JAVA_HOME=/usr/java/jdk1.8.0_144/

# Install maven
RUN wget http://ftp.meisei-u.ac.jp/mirror/apache/dist/maven/maven-3/3.5.0/binaries/apache-maven-3.5.0-bin.tar.gz
RUN tar xzvf apache-maven-3.5.0-bin.tar.gz
RUN rm apache-maven-3.5.0-bin.tar.gz
RUN ln -s apache-maven-3.5.0 maven
ENV M2_HOME=~/maven
ENV PATH=${M2_HOME}/bin:${PATH}

WORKDIR /projects

CMD ["mysqld"]
