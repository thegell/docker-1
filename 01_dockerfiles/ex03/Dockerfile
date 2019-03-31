#docker build -t gitlab .

#docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged gitlab

FROM ubuntu

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install -y ca-certificates openssh-server curl postfix

RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh > script.deb.sh

RUN chmod 777 script.deb.sh && ./script.deb.sh && apt-get install -y gitlab-ce

RUN apt update && apt install -y tzdata && \
	apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 443 80 22

RUN echo '/opt/gitlab/embedded/bin/runsvdir-start &gitlab-ctl reconfigure && sleep infinity' > ./start.sh

ENTRYPOINT ["bash", "./start.sh"]
