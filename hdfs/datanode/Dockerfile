FROM kerios/hdfs:2.9.2

LABEL author="kerios <abidikhairi32@gmail.com>"

HEALTHCHECK CMD curl -f http://localhost:500575/ || exit 1

ENV HDFS_CONF_dfs_datanode_data_dir=file:///hadoop/dfs/data
RUN mkdir -p /hadoop/dfs/data
VOLUME /hadoop/dfs/data

ADD run.sh /run.sh
RUN chmod a+x /run.sh

EXPOSE 50075

CMD ["/run.sh"]