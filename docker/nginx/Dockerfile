FROM nginx:1.26.0-alpine3.19-slim

ARG app_type
ENV app_type=${app_type}

COPY ./docker/nginx/default.${app_type}.conf /etc/nginx/conf.d/default.conf
