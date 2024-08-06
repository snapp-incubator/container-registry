# Use a Debian base image
FROM debian:stable-slim

# Set the desired version of the OpenShift CLI
ENV OC_VERSION=latest

# Install dependencies
RUN apt-get update && apt-get install -y curl tar && rm -rf /var/lib/apt/lists/*

# Download and install the OpenShift CLI
RUN curl -LO https://mirror.openshift.com/pub/openshift-v4/clients/oc/${OC_VERSION}/linux/oc.tar.gz && \
    tar -xzvf oc.tar.gz && \
    mv oc /usr/local/bin/ && \
    rm oc.tar.gz

# Verify the installation
RUN oc version
