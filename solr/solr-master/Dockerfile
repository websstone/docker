FROM java:openjdk-8-jre
MAINTAINER Siarhei Kamenchuk

ENV SOLR_USER solr
ENV SOLR_VERSION 5.2.1
ENV SOLR solr-$SOLR_VERSION

RUN apt-get update && \
	apt-get -y install lsof

RUN groupadd -r $SOLR_USER && \
	useradd -r -g $SOLR_USER $SOLR_USER

RUN mkdir -p /opt && \
	wget -nv --output-document=/opt/$SOLR.tgz http://www.us.apache.org/dist/lucene/solr/$SOLR_VERSION/$SOLR.tgz && \
	tar -C /opt --extract --file /opt/$SOLR.tgz && \
	rm /opt/$SOLR.tgz && \
	mv /opt/$SOLR /opt/solr && \
	chown -R $SOLR_USER:$SOLR_USER /opt/solr 

EXPOSE 8983
WORKDIR /opt/solr
USER $SOLR_USER
CMD ["/bin/bash", "-c", "/opt/solr/bin/solr -f"]