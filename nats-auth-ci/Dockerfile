# Use a lightweight Alpine base image
FROM alpine:3.20.0

# Install necessary dependencies
RUN apk add --no-cache \
    curl \
    git \
    bash \
    libc6-compat \
    jq \
    gnupg \ 
    sops \ 
    yq \ 
    nats-server

RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser
WORKDIR /dir
# Set the entrypoint (optional, adjust as needed)
ENTRYPOINT ["sh"]