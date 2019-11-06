### Usage
- build Docker image for elasticsearch and Kibana
```
docker-compose build
```
- turn up elasticsearch and Kibana
```
docker-compose up -d
```
Kibana is accessible on the http://localhost:5601
  
- turn down elasticsearch and Kibana
```
docker-compose down -v
```
 
### Elasticsearch Settings
 
There are some necessary configurations defined in docker-compose.yml
 
- cluster: single or multi-nodes in a cluster
```
discovery.type=single-node
```
- ulimits for nofile and noproc: have to be 65535 respectively
```
--ulimit nofile=65535:65535
```
- disable swapping: swapping needs to be disabled for performance and node stability
```
-e "bootstrap.memory_lock=true" --ulimit memlock=-1:-1
```
- set the heap size: ES_JAVA_OPTS environment vaiable can be used to set
```
-e ES_JAVA_OPTS="-Xms256m -Xmx256m" with docker run
```

