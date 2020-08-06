# Stage 1
FROM node:12 as builder

RUN apt-get update && apt-get install make -y

ADD . /app
WORKDIR /app

RUN make publish

# Stage 2
FROM nginx:stable

COPY --from=builder --chown=nginx:nginx /app /app
WORKDIR /app
ADD docker/nginx.conf /etc/nginx/conf.d/default.conf
