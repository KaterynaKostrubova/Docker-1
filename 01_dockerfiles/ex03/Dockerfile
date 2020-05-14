FROM ubuntu:16.04
MAINTAINER kkostrub <kkostrub@student.unit.ua>

# Install required packages
RUN apt-get update -q && apt-get upgrade -y && \
DEBIAN_FRONTEND=noninteractive apt-get install -y ca-certificates openssh-server wget postfix

# Download & Install GitLab
RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && chmod 777 script.deb.sh && ./script.deb.sh 
RUN EXTERNAL_URL="http://gitlab.example.com" apt-get install -y gitlab-ce

RUN apt update && apt install -y tzdata && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Expose web & ssh
EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null