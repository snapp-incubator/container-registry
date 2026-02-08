FROM alpine:3.23

RUN apk add --no-cache \
  curl \
  git \
  bash \
  libc6-compat \
  jq \
  yq \
  nats-server \
  unzip \
  libcap

RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser
WORKDIR /dir
SHELL ["/bin/bash", "-c"]
ENTRYPOINT ["/bin/sh"]
