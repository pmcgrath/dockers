# Based on 
#	https://github.com/nickstenning/dockerfiles/blob/master/graphite/Dockerfile
#	https://github.com/mattbaird/docker-statsd/blob/master/Dockerfile
#
FROM ubuntu:12.04
RUN echo 'deb http://us.archive.ubuntu.com/ubuntu/ precise universe' >> /etc/apt/sources.list
RUN apt-get update

# Software
RUN apt-get -y install python-ldap python-cairo python-django python-twisted python-django-tagging python-simplejson python-memcache python-pysqlite2 python-support python-pip gunicorn 
RUN apt-get -y install python-software-properties	# Required for adding ppa's later
RUN apt-get -y install nginx-light
RUN apt-get -y install git
RUN apt-get -y install vim
RUN apt-get -y install supervisor

# Node specific - See https://github.com/joyent/node/wiki/Installing-Node.js-via-package-manager
RUN add-apt-repository ppa:chris-lea/node.js
RUN apt-get update
RUN apt-get -y install nodejs

# Graphite software
RUN pip install whisper
RUN pip install carbon
RUN pip install graphite-web

# Statsd - Wasn't able to use npm
RUN git clone https://github.com/etsy/statsd.git /opt/statsd

# Configuration files
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf
ADD nginx.conf /etc/nginx/nginx.conf
ADD carbon.conf /opt/graphite/conf/carbon.conf
ADD storage-schemas.conf /opt/graphite/conf/storage-schemas.conf
ADD local_settings.py /opt/graphite/webapp/graphite/local_settings.py
ADD config.js /opt/statsd/config.js

# Set various permissions
RUN touch /opt/graphite/storage/graphite.db
RUN touch /opt/graphite/storage/index
RUN chown -R www-data /opt/graphite/storage
RUN chmod 0775 /opt/graphite/storage
RUN chmod 0775 /opt/graphite/storage/whisper
RUN chmod 0664 /opt/graphite/storage/graphite.db
RUN cd /opt/graphite/webapp/graphite && python manage.py syncdb --noinput

# Ports
EXPOSE :80
EXPOSE :2003
EXPOSE :2004
EXPOSE :7002
EXPOSE :8125/udp
EXPOSE :8126

# Pending
#volumes\data
#cmd
