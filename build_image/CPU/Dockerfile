FROM jerryzj/dev_basic:latest
# You may use other base images instead
# The following steps are enabling ssh service and setup
# default root login password

RUN apt-get update
RUN apt-get upgrade -y 
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd

RUN echo 'root:root' | chpasswd

RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/g' /etc/ssh/sshd_config
RUN mkdir /root/.ssh

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 22
CMD    ["/usr/sbin/sshd", "-D"]
