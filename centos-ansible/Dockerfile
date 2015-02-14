FROM camilobermudez85/vagrant-centos:centos-latest
MAINTAINER Camilo Bermudez <camilobermudez85@gmail.com>

# Install latest ansible available from yum
RUN yum clean all
RUN yum install -y epel-release && yum install -y ansible svn git

# Configure ansible hosts
RUN printf '[local]\nlocalhost\n' > /etc/ansible/hosts
