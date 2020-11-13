FROM openjdk:10

# A merge of:
#  https://github.com/zhilvis/docker-h2
#  https://github.com/zilvinasu/h2-dockerfile

MAINTAINER Oscar Fonts <oscar.fonts@geomati.co>
ENV H2_VERSION=1.4.200
ENV DOWNLOAD https://repo1.maven.org/maven2/com/h2database/h2/${H2_VERSION}/h2-${H2_VERSION}.jar
ENV DATA_DIR /opt/h2-data

RUN mkdir -p ${DATA_DIR} \
    && curl ${DOWNLOAD} -o /opt/h2.jar

COPY h2.server.properties /root/.h2.server.properties

EXPOSE 81 1521 9092

WORKDIR /opt/h2-data

CMD java -classpath /opt/h2.jar org.h2.tools.Server \
 	-tcp -tcpAllowOthers  \
 	-baseDir ${DATA_DIR} ${H2_OPTIONS}
