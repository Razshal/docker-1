FROM ruby

WORKDIR /root
RUN apt-get update && apt-get install -y --no-install-recommends curl openssh-server ca-certificates software-properties-common nginx
RUN wget --content-disposition https://packages.gitlab.com/gitlab/gitlab-ce/packages/debian/stretch/gitlab-ce_10.5.2-ce.0_amd64.deb/download.deb
RUN EXTERNAL_URL="http://192.168.99.1000" && dpkg -i gitlab-ce_10.5.2-ce.0_amd64.deb
RUN chmod go-w /usr/local/bundle/
RUN chmod go-w /usr/local/bundle/bin
RUN gitlab-ctl start
#RUN apt-get update && apt-get install -y curl openssh-server ca-certificates software-properties-common postfix
#RUN add-apt-repository ppa:chris-lea/redis-server
#RUN echo "deb http://ftp.utexas.edu/dotdeb/ stable all" > /etc/apt/sources.list.d/dotdeb.list
#RUN echo "deb-src http://ftp.utexas.edu/dotdeb/ stable all" >> /etc/apt/sources.list.d/dotdeb.list
#RUN wget https://www.dotdeb.org/dotdeb.gpg && apt-key add dotdeb.gpg
#RUN apt-get update && apt-get install -y --allow-unauthenticated redis-server
#RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

#RUN EXTERNAL_URL="http://192.168.99.1000" apt-get install gitlab-ce
