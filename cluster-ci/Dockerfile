FROM hashicorp/terraform:1.5.4

ARG TERRAFORM_PLUGIN_DIR=/terraform-plugins

ADD . /src

WORKDIR /src/shared-resources

RUN mkdir -p ${TERRAFORM_PLUGIN_DIR} && \
    # Install Terraform modules
    terraform get && \
    # Save local copies of all required provider plugins to ${TERRAFORM_PLUGIN_DIR}
    terraform providers mirror -platform=linux_amd64 ${TERRAFORM_PLUGIN_DIR} && \
    rm -rf /src

WORKDIR ${TERRAFORM_PLUGIN_DIR}
