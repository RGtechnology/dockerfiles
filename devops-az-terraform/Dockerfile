# Proof of Concept: DevOps Environment with Azure-CLI and Terraform
#
# docker run --rm -it -v ~/docker_mapped/work:/work devops-az-terraform
#

FROM ubuntu:20.04
LABEL maintainer "RGtechnology@rammerstorfer.xyz"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install --no-install-recommends -y \
    apt-utils wget curl vim nano htop lsb-release apt-transport-https ca-certificates gnupg; \
    mkdir /work

# install azure-cli - based on https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt
RUN curl -sSL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/trusted.gpg.d/microsoft.gpg; \
    echo "deb [arch=$(dpkg --print-architecture)] https://packages.microsoft.com/repos/azure-cli/ $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/azure-cli.list; \
    apt-get update && apt-get install --no-install-recommends -y \
    azure-cli

 # install terraform
RUN curl -sSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor > /etc/apt/trusted.gpg.d/hashicorp.gpg; \
    echo "deb [arch=$(dpkg --print-architecture)] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | tee /etc/apt/sources.list.d/terraform.list; \
    apt-get update && apt-get install --no-install-recommends -y \
    terraform

VOLUME [ "/work" ]

WORKDIR /work
CMD ["bash"]