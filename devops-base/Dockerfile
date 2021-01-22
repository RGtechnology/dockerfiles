# Used as a base image to build containerized DevOps environments.
#
# docker run -it --rm -v ~/local_work:/work rgtechnology/devops-base
#
FROM ubuntu:20.04
LABEL maintainer "RGtechnology@rammerstorfer.xyz"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install --no-install-recommends -y \
    apt-utils wget curl vim nano htop lsb-release apt-transport-https ca-certificates gnupg; \
    mkdir /work

VOLUME [ "/work" ]

CMD ["bash"]
