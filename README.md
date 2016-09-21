# docker

##AEM

###aem-base
- docker build -t aem-base .

###aem-author
- docker build -t aem-author .
- docker run -p 4502:4502 -p 30303:30303 aem-author

###aem-publish
- docker build -t aem-publish .
- docker run -p 4503:4503 -p 30303:30303 aem-publish

##Solr

### solr-master
- docker build -t solr-master .
- docker run -p 8983:8983 solr-master

### solr-slave
- docker build -t solr-slave .
- docker run -p 8983:8983 solr-slave
 

##Docker Compose
- docker-compose up
