FROM alpine:3.5
LABEL maintainer="Alex Maldonado <calidadis@gmail.com>"
LABEL version="3.2"
LABEL name="mongodb"

RUN echo http://dl-4.alpinelinux.org/alpine/edge/testing >> /etc/apk/repositories \
    && apk add --no-cache mongodb \ 
    && rm /usr/bin/mongosniff /usr/bin/mongoperf

VOLUME /data/db
EXPOSE 27017 
COPY docker-entrypoint.sh /usr/local/bin/
RUN ln -s /usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

ENTRYPOINT [ "docker-entrypoint.sh" ]
CMD [ "mongod" ]