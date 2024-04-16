> https://github.com/apache/griffin/blob/master/griffin-doc/docker/griffin-docker-guide.md

$ sudo apt update
$ sudo apt install docker-compose
$ sudo sysctl -w vm.max_map_count=262144

$ docker pull apachegriffin/griffin_spark2:0.3.0
$ docker pull apachegriffin/elasticsearch
$ docker pull apachegriffin/kafka
$ docker pull zookeeper:3.5

$ docker-compose -f docker-compose-batch.yml up -d

$ docker container ls

> import jsons from apachegriffin/jsons to postman environment
> http://localhost:38080/api/v1/version

