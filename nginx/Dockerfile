FROM debian:jessie

RUN truncate -s 0 /etc/apt/sources.list
RUN echo "deb http://mirrors.digitalocean.com/debian/ jessie main contrib non-free" >> /etc/apt/sources.list
RUN echo "deb http://mirrors.digitalocean.com/debian/ jessie-updates main contrib non-free" >> /etc/apt/sources.list
RUN apt-get update
RUN apt-get install -y apt-transport-https ca-certificates curl
RUN echo "deb https://deb.nodesource.com/node_6.x jessie main" >> /etc/apt/sources.list.d/nodesource.list
RUN echo "deb-src https://deb.nodesource.com/node_6.x jessie main" >> /etc/apt/sources.list.d/nodesource.list
RUN apt-get update 
RUN apt-get install -y nginx
RUN apt-get update
RUN apt-get install -y nano

RUN curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add -
RUN apt update
RUN apt install -y nodejs

ADD nginx.conf /etc/nginx/

ADD default /etc/nginx/sites-available/

RUN echo "upstream php-upstream { server php:9000; }" > /etc/nginx/conf.d/upstream.conf

RUN usermod -u 1000 www-data

CMD ["nginx"]

EXPOSE 80
EXPOSE 443
