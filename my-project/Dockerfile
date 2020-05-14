FROM openshift/base-centos7
MAINTAINER Jose Moreno
RUN yum install httpd -y
RUN yum install epel-release -y
RUN yum install python-pip -y
RUN pip install flask
RUN yum install mod_wsgi -y
RUN yum install mysql-devel -y
RUN yum install python-devel -y
RUN pip install flask-mysqldb
RUN pip install Flask-WTF
RUN pip install passlib
#RUN echo "WSGIScriptAlias / /var/www/proyecto/application.wsgi <VirtualHost *> ServerName www.servicios.com <Directory /var/www/proyecto/> Order deny,allow Allow from all </Directory> </VirtualHost>" > /etc/httpd/conf/httpd.conf
COPY httpd.conf/ /etc/httpd/conf/
WORKDIR /var/www/my-project/app/templates
#COPY db/ /var/www/my-project/db
COPY run.py/ /var/www/my-project
COPY config.py/ /var/www/my-project
COPY application.wsgi/ /var/www/my-project
COPY app /var/www/my-project/app
COPY app/templates /var/www/my-project/app/templates
RUN chmod -R 777 /var/www
#COPY httpd.conf/ /etc/httpd/conf/
EXPOSE 80
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
