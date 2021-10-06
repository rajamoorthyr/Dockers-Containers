FROM amazonlinux
MAINTAINER raj

RUN yum install -y openssh* sudo

RUN useradd raj && \
    echo raj:1234 | chpasswd && \
    mkdir /home/raj/.ssh && \
    chmod 700 /home/raj/.ssh && \
    usermod -u 1001 raj && groupmod -g 1001 raj && \
    usermod -a -G wheel raj

COPY raj.pub /home/raj/.ssh/authorized_keys

RUN chown raj:raj -R /home/raj/.ssh/ && \
    chmod 600 /home/raj/.ssh/authorized_keys

RUN /usr/sbin/sshd-keygen

CMD /usr/sbin/sshd -D
