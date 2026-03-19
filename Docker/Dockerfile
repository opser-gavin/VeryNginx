FROM ubuntu:22.04

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    wget perl make build-essential procps \
    libreadline-dev libncurses5-dev libpcre3-dev libssl-dev \
    liblua5.1-0-dev lua5.1 \
 && rm -rf /var/lib/apt/lists/*

RUN groupadd -r nginx && useradd -r -g nginx nginx

RUN mkdir /code
COPY . /code
WORKDIR /code
RUN python3 install.py install

EXPOSE 80

CMD ["/opt/verynginx/openresty/nginx/sbin/nginx", "-g", "daemon off; error_log /dev/stderr info;"]
