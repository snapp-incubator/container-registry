FROM quay.io/openstack.kolla/prometheus-libvirt-exporter:2025.1-ubuntu-noble

# Install dependencies for wget and tar
RUN apt-get update && apt-get install -y wget tar

# Set working directory
WORKDIR /

# Download and install prometheus-libvirt-exporter v2.2.0
RUN mkdir -p /prometheus-libvirt-exporter-source /opt/prometheus-libvirt-exporter && \
    wget https://github.com/inovex/prometheus-libvirt-exporter/releases/download/v2.2.0/prometheus-libvirt-exporter-2.2.0.linux-amd64.tar.gz -O /tmp/libvirt-exporter.tar.gz && \
    tar -xzf /tmp/libvirt-exporter.tar.gz -C /prometheus-libvirt-exporter-source --strip-components=1 && \
    ln -sfn /prometheus-libvirt-exporter-source /prometheus-libvirt-exporter && \
    cp /prometheus-libvirt-exporter/prometheus-libvirt-exporter /opt/libvirt-exporter && \
    chmod +x /opt/libvirt-exporter && \
    rm -rf /tmp/libvirt-exporter.tar.gz

# Entrypoint using dumb-init
ENTRYPOINT ["dumb-init", "--single-child", "--"]

# Default command
CMD ["kolla_start"]