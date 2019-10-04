FROM alpine:3.10
LABEL maintainer="Hu Yao"

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories && \
    apk update && \
    apk add --virtual build-dependencies build-base gcc g++ gdb cmake openssh rsync && \
    rm  -rf /tmp/* /var/cache/apk/*
# setup ssh server
RUN sed -i s/#PermitRootLogin.*/PermitRootLogin\ yes/ /etc/ssh/sshd_config
RUN echo 'root:root' |chpasswd

EXPOSE 22 7777

CMD ssh-keygen -A ; /usr/sbin/sshd -D