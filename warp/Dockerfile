FROM alpine

MAINTAINER MinIO Development "dev@min.io"

EXPOSE 7761

ADD https://dl.min.io/aistor/warp/release/linux-amd64/archive/warp.v1.5.0 /warp

RUN chmod +x /warp

ENTRYPOINT ["/warp"]
