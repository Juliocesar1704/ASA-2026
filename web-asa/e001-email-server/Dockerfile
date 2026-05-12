FROM debian:latest (last pushed 2 days ago)

RUN apt update -y
RUN apt upgrade -y

RUN apt install postfix dovecot-imapd dovecot-pop3d telnet nano syslog-ng -y

COPY ./postfix/* /etc/postfix
COPY ./dovecot/* /etc/dovecot/conf.d
COPY mailname /etc/mailname
COPY mail.sh /etc/init.d

RUN chmod 755 /etc/init.d/mail.sh

EXPOSE 25/tcp
EXPOSE 587/tcp
EXPOSE 110/tcp
EXPOSE 143/tcp

CMD ["sh", "-c", "service syslog-ng start ; service postfix start ; service dovecot start; tail -F /var/log/mail.log"]