# This image contains node and docker binaries to be used as the base image for the tasks 
# that require node, yarn and docker commands together.
FROM node:18-bookworm

RUN npm install npm@latest -g
RUN apt-get update && apt-get install -y \
    docker.io \
    && rm -rf /var/lib/apt/lists/*
