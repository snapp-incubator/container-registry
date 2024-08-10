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
    nats-server \ 
    unzip \ 
    libcap

RUN wget https://releases.hashicorp.com/vault/1.17.3/vault_1.17.3_linux_amd64.zip 
RUN unzip vault_1.17.3_linux_amd64.zip

RUN mv vault /usr/local/bin/
RUN chmod +x /usr/local/bin/vault
    
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser
WORKDIR /dir
# Set the entrypoint (optional, adjust as needed)
ENTRYPOINT ["sh"]