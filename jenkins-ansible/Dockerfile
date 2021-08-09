FROM jenkins/jenkins
USER root
RUN apt update
RUN apt install python3 python3-pip -y
RUN pip3 install -U ansible
USER jenkins
