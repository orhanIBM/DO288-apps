# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

#httpd cannot run on openshift with Root priv. listening ports below 1024

EXPOSE 8080
#this tells openshift that expose svc at 8080, based on EXPOSE command above 
#LABEL io.openshift.expose-services="8080:http"

#and add some metadata 
LABEL io.k8s.description="A basic Apache HTTP Server child image, uses ONBUILD" \
      io.k8s.display-name="Apache HTTP Server" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="apache, httpd"

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf

RUN chgrp -R 0 /var/log/httpd /var/run/httpd && chmod -R g=u /var/log/httpd /var/run/httpd

USER 1001
