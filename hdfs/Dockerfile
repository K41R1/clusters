FROM nimmis/java-centos:openjdk-8-jdk
LABEL author="kerios <abidikhairi32@gmail.com>"

ENV HADOOP_VERSION=2.9.2
ENV JAVA_HOME=/usr/lib/jvm/java-1.8.0

COPY hadoop.tar.gz /tmp

RUN yum install -y -q net-tools \
      curl \
      which \
      netcat \
      perl \
      gnupg \
RUN mkdir $HADOOP_HOME/logs \
    && yum clean all \
    && tar -xzvf /tmp/hadoop.tar.gz -C /opt/ \
    && rm -rf /tmp/hadoop.tar.gz

RUN ln -s /opt/hadoop/etc/hadoop /etc/hadoop

ENV HADOOP_CONF_DIR=/etc/hadoop
ENV HADOOP_HOME=/opt/hadoop
ENV MULTIHOMED_NETWORK=1
ENV USER=root
ENV PATH $HADOOP_HOME/bin/:$PATH
ENV PATH $HADOOP_HOME/sbin/:$PATH

RUN ln -s /usr/lib/jvm/java-1.8.0 /usr/lib/jvm/default

ADD entrypoint.sh /entrypoint.sh

RUN chmod a+x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]