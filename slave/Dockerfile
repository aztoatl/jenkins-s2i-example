# The FROM will be replaced when building in OpenShift
FROM ubuntu:latest

MAINTAINER Damian Zermeno <damian@miluchita.com.mx>

# Install headless Java
USER root
RUN apt-get update && apt-get install -y openjdk-8-jre-headless gettext tar git && mkdir -p /var/lib/jenkins && chown -R 1001:0 /var/lib/jenkins && chmod -R g+w /var/lib/jenkins

# Copy the entrypoint
WORKDIR configuration/
COPY . /var/lib/jenkins/
USER 1001

# Run the JNLP client by default
# To use swarm client, specify "/var/lib/jenkins/run-swarm-client" as Command
ENTRYPOINT ["/var/lib/jenkins/run-jnlp-client"]

RUN ls /var/lib/jenkins/
