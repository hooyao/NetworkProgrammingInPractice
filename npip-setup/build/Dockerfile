FROM gcc:9.2.0
LABEL maintainer="Hu Yao"

RUN echo "\
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ buster main contrib non-free\n\
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ buster-updates main contrib non-free\n\
deb https://mirrors.tuna.tsinghua.edu.cn/debian/ buster-backports main contrib non-free\n\
deb https://mirrors.tuna.tsinghua.edu.cn/debian-security buster/updates main contrib non-free\n\
" > /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y apt-utils g++ gdb gdbserver cmake openssh-server rsync && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
# Setup ssh server
RUN mkdir /var/run/sshd
RUN echo 'root:root' |chpasswd
RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config

RUN mkdir /root/.ssh

EXPOSE 22 7777

CMD ["/usr/sbin/sshd", "-D"]