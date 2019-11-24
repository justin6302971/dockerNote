FROM debian:stable
MAINTAINER justin6302971 <justin6302971@hotmail.com>

RUN apt-get update && apt-get upgrade -y && apt-get install -y apache2 telnet elinks openssh-server

ENV MYVALUE my-value

EXPOSE 80

CMD ["/usr/sbin/apache2ctl","-D","FOREGROUND"]