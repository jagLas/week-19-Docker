FROM ubuntu

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y npm nodejs

ADD . /app
RUN cd /app && npm install

CMD cd /app && npm start