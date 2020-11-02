# docker build -t ex03 .
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:8443 --privileged ex03
# docker run -it --rm -p 80:80 -p 7722:22 -p 443:443 --privileged ex03
# ssh -T -p 8022 git@192.168.99.106
# git -c http.sslVerify=false clone https://192.168.99.106:8443/vovan/awe.git
# git clone ssh://git@192.168.99.106:8022/vovan/awe.git

FROM ubuntu:18.04

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y wget \
        ca-certificates \
        openssh-server \
        postfix \
        tzdata && \
    apt-get -y clean

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && \
    chmod 777 script.deb.sh && ./script.deb.sh && \
    apt-get install -y gitlab-ce && \
    apt-get -y clean

ARG USER_URL="192.168.99.106"

EXPOSE 22 80 8443

RUN mkdir -p /etc/gitlab/ssl && \
	chmod 755 /etc/gitlab/ssl && \
	openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/gitlab/ssl/${USER_URL}.key -out /etc/gitlab/ssl/${USER_URL}.crt -subj "/C=UA/ST=A/L=A/O=school21/OU=docker/CN=${USER_URL}" && \
	chmod 600 /etc/gitlab/ssl/* && \
	sed -i "s/external_url 'http:\/\/gitlab.example.com'/external_url 'https:\/\/${USER_URL}:8443'/" /etc/gitlab/gitlab.rb && \
    sed -i "s/# nginx\['redirect_http_to_https'\] = false/nginx\['redirect_http_to_https'\] = true/" /etc/gitlab/gitlab.rb

RUN mkdir -p /run/sshd

ENTRYPOINT service ssh start && (/opt/gitlab/embedded/bin/runsvdir-start &)  && /usr/sbin/sshd &&  gitlab-ctl reconfigure && tail -f /dev/null
