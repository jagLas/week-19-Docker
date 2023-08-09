docker container run --name nginx -d -p 80:80 nginx

docker container run --name httpd -d -p 81:80 httpd

docker container run --name mysql -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=password mysql

docker container inspect mysql

docker container stop mysql nginx httpd 

docker container rm 
or
docker container prune

docker container run -it --name web nginx bash
<!-- temporary -->

docker container start web
docker container exec -it web bash
<!-- keeps it persisting -->

docker container run --name ubuntu -d -t ubuntu
docker exec -i ubuntu bash

docker container run --name characters -d -t alpine
docker container exec -d characters /bin/sh -c "while :; do wget -qO- https://swapi.dev/api/people/?search=r2; printf '\n'; sleep 5s; done"


docker network create --driver bridge funtime
docker container run -d --net funtime --name elastic elasticsearch:2
docker container run -d --net funtime --name elastic2 elasticsearch:2


docker container run -d --network funtime --network-alias partytime --name elastic elasticsearch:2

docker container run --name alpine --network funtime --network-alias partytime -d -t alpine
docker exec -i alpine sh

docker run -d -i --network funtime --network-alias partytime --name cent centos curl partytime:9200
docker start cent
docker container logs cent