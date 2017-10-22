FROM centos:centos7

MAINTAINER http://www.centos.org
LABEL Vendor="CentOS"
LABEL License=GPLv2
LABEL Version=2.4.6-31

RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
RUN yum -y update && yum clean all
RUN yum -y install git gcc gcc-c++ autoconf automake make zip php71w-devel php71w-pear httpd php71w php71w-pdo php71w-mysql php71w-xml && yum clean all
RUN pecl install Xdebug

COPY httpd.conf /etc/httpd/conf/httpd.conf
COPY php.ini /etc/php.ini
COPY xdebug.ini /etc/php.d/xdebug.ini

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php composer-setup.php && php -r "unlink('composer-setup.php');"


RUN echo 'cd /var/www/html' >> ~/.bashrc
EXPOSE 80

# Simple startup script to avoid some issues observed with container restart 
ADD run-httpd.sh /run-httpd.sh
RUN chmod -v +x /run-httpd.sh

CMD ["/run-httpd.sh"]
