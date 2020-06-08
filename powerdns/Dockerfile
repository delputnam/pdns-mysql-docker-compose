FROM ubuntu:latest

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y && \
    apt-get install -y mariadb-client && \
    apt-get install -y pdns-server pdns-backend-mysql && \
# Clean up APT when done.
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 53/tcp
EXPOSE 53/udp
EXPOSE 8081/tcp

ADD ./pdns.sql /

ADD ./start.sh /
RUN chmod +x /start.sh

ENTRYPOINT ["/start.sh"]
