FROM alpine:3.17.3 as schemas
ARG kubeconform_version=0.6.1
ARG helm_version=3.8.0
ARG kyverno_cli_version=1.10.0
WORKDIR /
RUN apk --no-cache add git python3 jq git curl py-pip
RUN pip install pyyaml==6.0.1

## install kubeval, helm, yq, kyverno
RUN curl -SsL https://github.com/yannh/kubeconform/releases/download/v${kubeconform_version}/kubeconform-linux-amd64.tar.gz | tar xz -C /tmp &&\
    mv /tmp/kubeconform /usr/local/bin/kubeconform &&\
    curl -SsL https://get.helm.sh/helm-v${helm_version}-linux-amd64.tar.gz | tar xz -C /tmp && \
    mv /tmp/linux-amd64/helm /usr/local/bin/helm &&\
    curl -SsL https://github.com/mikefarah/yq/releases/download/v4.21.1/yq_linux_amd64.tar.gz | tar xz -C /tmp &&\
    mv /tmp/yq_linux_amd64 /usr/local/bin/yq &&\
    rm -Rf /tmp/* &&\
    wget https://github.com/kyverno/kyverno/releases/download/v1.10.0/kyverno-cli_v1.10.0_linux_x86_64.tar.gz &&\
    tar -xzpf kyverno-cli_v${kyverno_cli_version}_linux_x86_64.tar.gz && chmod +x kyverno && mv kyverno /usr/bin/

COPY ./scheme.tar.gz /scheme.tar.gz
RUN tar xzpf scheme.tar.gz

ENTRYPOINT [ "/bin/sh" ]
