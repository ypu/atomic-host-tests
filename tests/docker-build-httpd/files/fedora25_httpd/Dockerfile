FROM registry.fedoraproject.org/fedora:25
MAINTAINER Micah Abbott <micah@redhat.com>

LABEL Version=1.2
LABEL RUN="docker run -d --name NAME -p 80:80 IMAGE"

ENV container docker

COPY Dockerfile /root/
COPY makecache.sh /root/

RUN /root/makecache.sh && \
    dnf -y install httpd && \
    dnf clean all

RUN echo "SUCCESS fedora25_httpd" > /var/www/html/index.html
EXPOSE 80

ENTRYPOINT [ "/usr/sbin/httpd" ]
CMD [ "-D", "FOREGROUND" ]
