docker build . -t jaglas/node-server
docker container run --name node -d -p 8000:8000 jaglas/node-server:latest