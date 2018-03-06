FROM ruby:2.3.6

WORKDIR /root
RUN apt-get update && apt-get install -y --no-install-recommends curl openssh-server ca-certificates software-properties-common nginx gnupg
#RUN wget --content-disposition https://packages.gitlab.com/gitlab/gitlab-ce/packages/debian/stretch/gitlab-ce_10.5.2-ce.0_amd64.deb/download.deb
#RUN export EXTERNAL_URL="http://192.168.99.1000" && dpkg -i gitlab-ce_10.5.2-ce.0_amd64.deb
#RUN chmod go-w /usr/local/bundle/
#RUN chmod go-w /usr/local/bundle/bin
#RUN gitlab-ctl start

RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash
#RUN EXTERNAL_URL="http://192.168.99.1000" apt-get install gitlab-ce
