FROM registry.redhat.io/openshift3/jenkins-slave-base-rhel7:v3.11

MAINTAINER Andrew Block <ablock@redhat.com>

LABEL com.redhat.component="jenkins-slave-image-mgmt" \
      name="jenkins-slave-image-mgmt" \
      architecture="x86_64" \
      io.k8s.display-name="Jenkins Slave Image Management" \
      io.k8s.description="Image management tools on top of the jenkins slave base image" \
      io.openshift.tags="openshift,jenkins,slave,copy"
USER root

RUN yum -y localinstall https://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/e/epel-release-7-11.noarch.rpm && \
    yum-config-manager --add-repo=http://mirror.centos.org/centos/7.6.1810/os/x86_64/ \
      --add-repo=http://mirror.centos.org/centos/7.6.1810/extras/x86_64/ && yum repolist all

RUN INSTALL_PKGS="skopeo" && \
    yum install -y --setopt=tsflags=nodocs --nogpgcheck \
    $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all

USER 1001
