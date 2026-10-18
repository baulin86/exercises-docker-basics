FROM ubuntu:24.04 

WORKDIR /usr/src/app

COPY script.sh .


RUN apt-get update && apt-get install curl -y

CMD ./script.sh

