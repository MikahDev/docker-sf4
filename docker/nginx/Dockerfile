FROM nginx:1.15.8-alpine
 
RUN apk add --no-cache bash
 
RUN rm -rf /var/cache/apk/*
 
COPY app.conf /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/nginx.conf
COPY app_ssl.crt /etc/ssl/certs/app_ssl.crt
COPY app_ssl.key /etc/ssl/private/app_ssl.key