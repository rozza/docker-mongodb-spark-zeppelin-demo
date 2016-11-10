FROM ubuntu:16.04

RUN apt-get update && apt-get install -y --no-install-recommends \
openjdk-8-jdk-headless \
openjdk-8-jre-headless \
libfontconfig \
git \
maven \
wget

# ZEPPELIN
ENV ZEPPELIN_VERSION      0.6.1
ENV ZEPPELIN_HOME         /zeppelin
ENV ZEPPELIN_CONF_DIR     $ZEPPELIN_HOME/conf
ENV ZEPPELIN_NOTEBOOK_DIR $ZEPPELIN_HOME/notebook
ENV ZEPPELIN_PORT         8080

RUN wget http://www.mirrorservice.org/sites/ftp.apache.org/zeppelin/zeppelin-${ZEPPELIN_VERSION}/zeppelin-${ZEPPELIN_VERSION}.tgz && \
    tar xvf zeppelin-${ZEPPELIN_VERSION}.tgz
RUN rm -fv zeppelin-${ZEPPELIN_VERSION}.tgz
RUN mv zeppelin-${ZEPPELIN_VERSION} $ZEPPELIN_HOME

# INSTALL & CLEAN
WORKDIR ${ZEPPELIN_HOME}
RUN dev/change_scala_version.sh 2.11
RUN mvn -Pscala-2.11 -Pspark-2.0 -Phadoop-2.6 -Pyarn -Ppyspark -Psparkr -Pscala-2.11 -Dhadoop.version=2.6.0 -DskipTests clean package

# Copy over the files
RUN rm -rf notebook
COPY files/notebook notebook
COPY files/data data
COPY files/img zeppelin-web/dist/assets/images

CMD "bin/zeppelin.sh"