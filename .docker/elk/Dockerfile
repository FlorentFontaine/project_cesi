FROM sebp/elk:7.10.0


# Filebeat 7.11.1
###############################################################################
#                                INSTALLATION
###############################################################################

### install Filebeat

ENV FILEBEAT_VERSION 7.11.1
ENV FILEBEAT_BASE_VERSION 7.11.1


RUN apt-get update -qq \
 && apt-get install -qqy curl \
 && apt-get clean

RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-${FILEBEAT_VERSION}-amd64.deb \
 && dpkg -i filebeat-${FILEBEAT_VERSION}-amd64.deb \
 && rm filebeat-${FILEBEAT_VERSION}-amd64.deb


###############################################################################
#                                CONFIGURATION
###############################################################################


### configure Filebeat

# config file
ADD filebeat/filebeat.yml /etc/filebeat/filebeat.yml
RUN chmod 644 /etc/filebeat/filebeat.yml

ADD filebeat/modules/apache-access.yml /etc/filebeat/modules.d/apache-access.yml
RUN chmod 644 /etc/filebeat/modules.d/apache-access.yml

ADD filebeat/modules/apache-error.yml /etc/filebeat/modules.d/apache-error.yml
RUN chmod 644 /etc/filebeat/modules.d/apache-error.yml


#CMD  exec filebeat -e -c /etc/filebeat/filebeat.yml

#COPY start.sh /usr/local/bin/start.sh
#RUN chmod +x /usr/local/bin/start.sh
#ENTRYPOINT /usr/local/bin/start.sh
#CMD ["echo", "OK"]

#CMD ["filebeat", "-e", "-c", "/etc/filebeat/filebeat.yml"]

#CMD [ "/usr/local/bin/start.sh" ]
#ADD docker-entrypoint.sh /opt/
#RUN chmod +x /opt/docker-entrypoint.sh
#ENTRYPOINT ["/opt/docker-entrypoint.sh"]
#CMD ["start"]

#&& filebeat -e -c /etc/filebeat/filebeat.yml -d "publish"

