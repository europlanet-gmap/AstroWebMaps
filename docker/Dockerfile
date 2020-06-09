# Stage 1
FROM debian:stable-slim

RUN apt-get update && apt-get install make -y

ADD . /app
WORKDIR /app

RUN make

# Stage 2
FROM nginx:stable

COPY --from=0 --chown=nginx:nginx /app /app
WORKDIR /app
ADD docker/nginx.conf /etc/nginx/conf.d/default.conf
