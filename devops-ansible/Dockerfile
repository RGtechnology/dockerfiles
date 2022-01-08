# Proof of Concept: DevOps Environment with Ansible
#
# docker run -it --rm -v ~/docker/ansible:/work rgtechnology/devops-ansible
#

FROM ubuntu:20.04
LABEL maintainer "RGtechnology@rammerstorfer.xyz"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install --no-install-recommends -y \ 
    apt-utils wget curl vim nano htop lsb-release iputils-ping apt-transport-https ca-certificates gnupg2 python3-pip sshpass git rsync openssh-client && \
    rm -rf /var/lib/apt/lists/* && \
    apt-get clean

# install Ansible
RUN pip3 install ansible==4.1 && \
    pip3 install --upgrade pywinrm mitogen ansible-lint jmespath && \
    rm -rf /root/.cache/pip

VOLUME ["/work"] 
WORKDIR /work

CMD ["bash"]