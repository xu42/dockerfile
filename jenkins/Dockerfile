FROM jenkins/jenkins:lts
USER root

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update

RUN apt-get install -y --no-install-recommends apt-utils
RUN apt-get install -y git sudo curl wget gcc g++ make

# python
RUN apt-get install -y python3 python3-pip

# nodejs for frontend project
RUN curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
RUN apt-get install -y nodejs
RUN curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | gpg --dearmor | tee /usr/share/keyrings/yarnkey.gpg >/dev/null
RUN echo "deb [signed-by=/usr/share/keyrings/yarnkey.gpg] https://dl.yarnpkg.com/debian stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install -y yarn

# java for backend project
RUN apt-get install -y default-jdk maven

# test
RUN java -version && mvn -version && node --version && yarn --version

# docker build -t wrap/jenkins:lts .
# docker run -d --name jenkins -p 8080:8080 -v /home/app/jenkins_data/:/var/jenkins_home --restart=always --user 1000:1000 wrap/jenkins:lts
