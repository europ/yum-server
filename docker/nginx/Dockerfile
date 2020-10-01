FROM nginx:1-alpine

RUN ln -fs /usr/share/zoneinfo/Europe/Prague /etc/localtime
RUN rm /etc/nginx/conf.d/default.conf

COPY ./nginx/certs/* /etc/nginx/certs/
COPY ./nginx/conf.d/* /etc/nginx/conf.d/

RUN nginx -t
