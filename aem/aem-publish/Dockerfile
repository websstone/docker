FROM aem-base
MAINTAINER Siarhei Kamenchuk

ENV CQ_RUNMODE publish,local,technical
ENV CQ_PORT 4503
ENV DEBUG_PORT 30303

EXPOSE $CQ_PORT $DEBUG_PORT

CMD $AEM_WORKING_DIR/crx-quickstart/bin/start
