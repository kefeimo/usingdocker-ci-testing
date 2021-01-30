FROM jenkins:2.60.3
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

USER jenkins