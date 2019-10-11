# The FROM will be replaced when building in OpenShift
FROM ubuntu:latest

MAINTAINER Damian Zermeno <damian@miluchita.com.mx>

# Install headless Java
USER root
RUN apt-get update && \
    export INSTALL_PKGS="nss_wrapper java-1.8.0-openjdk-headless \
        java-1.8.0-openjdk-devel nss_wrapper gettext tar git" && \
    apt-get install -y -setopt=tsflags=nodocs install $INSTALL_PKGS && \
    mkdir -p /var/lib/jenkins && \
    chown -R 1001:0 /var/lib/jenkins && \
    chmod -R g+w /var/lib/jenkins

# Copy the entrypoint
WORKDIR configuration/
COPY . /var/lib/jenkins/
USER 1001

# Run the JNLP client by default
# To use swarm client, specify "/var/lib/jenkins/run-swarm-client" as Command
ENTRYPOINT ["/var/lib/jenkins/run-jnlp-client"]
