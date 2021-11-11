ARG UBUNTU_VERSION=18.04
FROM ubuntu:${UBUNTU_VERSION}
ARG DOTNET_VERSION=5.0

RUN cd /tmp \
    && apt-get update \
    && apt install -y wget \
    && wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb \
    && dpkg -i packages-microsoft-prod.deb \
    && rm packages-microsoft-prod.deb \
    && apt-get update \
    && apt-get install -y apt-transport-https \
    && apt-get update  \
    && apt-get install -y aspnetcore-runtime-${DOTNET_VERSION} \
    && rm -rf /var/lib/apt/lists/* 

ENV \
    # Configure web servers to bind to port 80 when present
    ASPNETCORE_URLS=http://+:80 \
    # Enable detection of running in a container
    DOTNET_RUNNING_IN_CONTAINER=true