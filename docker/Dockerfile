############################################################
# Dockerfile for Sane-stack to run sails.js API application
############################################################
FROM node:8.1.1
MAINTAINER Sajil Koroth<sajil@kapitalwise.com>
RUN apt-get update && \
    apt-get install -y git
    
RUN apt-get install -y runit
CMD export > /etc/envvars && /usr/sbin/runsvdir-start
RUN echo 'export > /etc/envvars' >> /root/.bashrc
RUN npm install -g npm@4.1.2
RUN npm install sails -g
RUN npm install nodemon -g
RUN npm install grunt-cli -g
#RUN npm install -g sails grunt bower pm2 npm-check-updates

RUN npm install grunt -g 
RUN mkdir /test-project

# Define mountable directories.
#VOLUME ["/test-project"]

ADD . test-project
WORKDIR /test-project
COPY package.json /test-project
RUN npm install sails && npm install  sails-mysql-transactions
RUN cd /test-project
RUN npm install
# Expose ports.
EXPOSE 1337
WORKDIR /test-project
CMD ["./start.sh"]
