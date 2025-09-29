
FROM node:22-alpine AS builder
WORKDIR /build
COPY frontend/ /build/

FROM nginx:alpine
COPY frontend/nginx.conf /etc/nginx/conf.d/default.conf
COPY frontend/index.html /usr/share/nginx/html/index.html
COPY frontend/main.js   /usr/share/nginx/html/main.js
EXPOSE 80
