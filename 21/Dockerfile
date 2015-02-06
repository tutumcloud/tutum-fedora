FROM fedora:21
MAINTAINER Fernando Mayo <fernando@tutum.co>

# Install packages and set up sshd
RUN yum -y install openssh-server pwgen
RUN rm -f /etc/ssh/ssh_*_key && ssh-keygen -q -N "" -t dsa -f /etc/ssh/ssh_host_dsa_key && ssh-keygen -q -N "" -t rsa -f /etc/ssh/ssh_host_rsa_key && sed -i "s/#*UsePrivilegeSeparation.*/UsePrivilegeSeparation no/g" /etc/ssh/sshd_config && ssh-keygen -q -N "" -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key && sed -i "s/#*UseDNS.*/UseDNS no/g" /etc/ssh/sshd_config

# Add scripts
ADD set_root_pw.sh /set_root_pw.sh
ADD run.sh /run.sh
RUN chmod +x /*.sh

EXPOSE 22
CMD ["/run.sh"]
