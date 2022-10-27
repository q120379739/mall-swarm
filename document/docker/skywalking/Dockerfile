FROM alpine:3.8

LABEL maintainer="120379739@qq.com"


ADD https://archive.apache.org/dist/skywalking/java-agent/8.9.0/apache-skywalking-java-agent-8.9.0.tgz /

RUN tar -zxvf /apache-skywalking-java-agent-8.9.0.tgz && \
    mv skywalking-agent skywalking && \
    mv /skywalking/optional-plugins/apm-trace-ignore-plugin* /skywalking/plugins/ && \
    echo -e "\n# Ignore Path" >> /skywalking/config/agent.config && \
    echo "# see https://github.com/apache/skywalking/blob/v8.1.0/docs/en/setup/service-agent/java-agent/agent-optional-plugins/trace-ignore-plugin.md" >> /skywalking/config/agent.config && \
    echo 'trace.ignore_path=${SW_IGNORE_PATH:/health}' >> /skywalking/config/agent.config