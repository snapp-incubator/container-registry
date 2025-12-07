FROM docker.io/fluent/fluentd:v1.19-2

USER root

RUN fluent-gem install fluent-plugin-unix-client \
    && fluent-gem install fluent-plugin-opensearch \
    && fluent-gem install fluent-plugin-multi-format-parser \
    && fluent-gem install fluent-plugin-prometheus

USER fluent
