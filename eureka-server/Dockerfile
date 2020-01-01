FROM java:8-jdk-alpine
LABEL maintainer gtopit.com
ENV JAVA_OPTS="$JAVA_OPTS -Dfile.encoding=UTF8 -Duser.timezone=GMT+08"
RUN  apk add -U tzdata && \
     ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
COPY ./target/eureka-server.jar /
COPY pinpoint /pinpoint
EXPOSE 8761
CMD java -jar -javaagent:/pinpoint/pinpoint-bootstrap-1.8.3.jar -Dpinpoint.agentId=${HOSTNAME} -Dpinpoint.applicationName=eureka-server $JAVA_OPTS -Deureka.instance.hostname=${MY_POD_NAME}.eureka.wb-parking /eureka-server.jar
