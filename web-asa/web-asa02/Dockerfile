FROM ubuntu:latest

RUN apt update -y && apt install bind9 dnsutils -y

COPY named.conf.local /etc/bind/named.conf.local
COPY jc.asa.br /etc/bind/jc.asa.br

RUN chown -R bind:bind /etc/bind

EXPOSE 5353/tcp
EXPOSE 5353/udp

CMD ["/usr/sbin/named", "-g", "-c", "/etc/bind/named.conf.local", "-u", "bind"]