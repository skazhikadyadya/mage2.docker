FROM debian:stretch-backports

ARG SHOP_URI

RUN apt-get update && apt-get upgrade -y

RUN apt-get install -y letsencrypt -t stretch-backports \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* \
  && mkdir -p /etc/nginx/ssl/ \
  && openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
    -keyout /etc/nginx/ssl/privkey.pem \
    -out /etc/nginx/ssl/fullchain.pem \
    -subj /CN=${SHOP_URI}