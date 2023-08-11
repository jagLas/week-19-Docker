FROM ubuntu

ADD . /app

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y npm nodejs

RUN cd /app && npm install

CMD cd /app && npm start