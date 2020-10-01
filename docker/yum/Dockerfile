FROM centos:7

RUN ln -fs /usr/share/zoneinfo/CET /etc/localtime

RUN yum -y update && \
    yum -y install epel-release && \
    yum -y install createrepo nginx rpm-sign rng-tools && \
    yum clean all

COPY ./yum/nginx.conf /etc/nginx/nginx.conf
COPY ./yum/repository.repo /etc/yum.repos.d/repository.repo

CMD ["/bin/bash", "-c", "createrepo /yum && nginx -g 'daemon off;'"]
