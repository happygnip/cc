FROM jenkins_php:v1

ENV TZ=Asia/Shanghai
USER root
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

USER jenkins
