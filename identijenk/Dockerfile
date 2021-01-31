FROM jenkins/jenkins:lts
USER root

RUN     apt-get update \
     && apt-get install -y \
        sudo \
	apt-transport-https \
	ca-certificates \
	curl \
        gnupg-agent \
        software-properties-common \
	 
     && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
     && add-apt-repository \
        "deb [arch=amd64] https://download.docker.com/linux/debian \
        $(lsb_release -cs) \
        stable"
	 
RUN  apt-get update \
     && apt-get install -y docker-ce
	 
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

# RUN curl -L https://github.com/docker/compose/releases/download/1.4.1/\
# docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose; \
# chmod +x /usr/local/bin/docker-compose
RUN apt-get install -y docker-compose

USER jenkins

# COPY plugins.txt /usr/share/jenkins/plugins.txt
# RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
# install plugin
RUN /usr/local/bin/install-plugins.sh scm-api git-client git greenballs
