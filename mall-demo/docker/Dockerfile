FROM registry.cn-beijing.aliyuncs.com/xngczl/oraclejdk-linux-64:1.8.0_261
VOLUME /tmp
ADD ./maven/mall-demo-1.0-SNAPSHOT.jar app.jar
RUN bash -c 'touch /app.jar'
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' >/etc/timezone
ENTRYPOINT ["java","-Dapp.id=svc-mall-demo","-javaagent:/var/logs/skywalking-agent.jar","-Dskywalking.agent.service_name=svc-mall-demo","-Dskywalking.collector.backend_service=172.16.33.163:11800","-Dcom.sun.management.jmxremote","-Dcom.sun.management.jmxremote.authenticate=false","-Dcom.sun.management.jmxremote.ssl=false","-Dcom.sun.management.jmxremote.port=1103","-Dcom.sun.management.jmxremote.rmi.port=1103","-Djava.rmi.server.hostname=localhost","-jar","-Dspring.profiles.active=prod","-Djava.security.egd=file:/dev/./urandom","/app.jar"]