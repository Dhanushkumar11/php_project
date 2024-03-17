FROM jenkins/jenkins:lts
USER root
RUN apt-get update && apt-get install -y lsb-release wget
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
RUN wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-5.0.1.3006-linux.zip && \
    unzip -qq sonar-scanner-cli-5.0.1.3006-linux.zip && \
    rm -rf sonar-scanner-cli-5.0.1.3006-linux.zip && \
    mv sonar-scanner-5.0.1.3006-linux /var/jenkins_home/sonar-scanner
ENV PATH $PATH:/var/jenkins_home/sonar-scanner/bin

USER jenkins
