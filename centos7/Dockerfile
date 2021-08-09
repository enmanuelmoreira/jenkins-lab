FROM centos:7

RUN yum -y install openssh-server

RUN useradd remote-user && \
    echo "1234" | passwd remote-user  --stdin && \
    mkdir /home/remote-user/.ssh && \
    chmod 700 /home/remote-user/.ssh

COPY remote-key.pub /home/remote-user/.ssh/authorized_keys

RUN chown remote-user:remote-user   -R /home/remote-user && \
    chmod 600 /home/remote-user/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen > /dev/null 2>&1

RUN yum -y install mysql && \
    yum -y install epel-release && \
    yum -y install python3 python3-pip && \
    pip3 install --upgrade pip && \
    pip3 install awscli

CMD /usr/sbin/sshd -D

