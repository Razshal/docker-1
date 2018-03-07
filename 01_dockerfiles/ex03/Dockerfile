FROM ubuntu:14.04

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates openssh-server wget apt-transport-https
RUN echo "deb https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ `lsb_release -cs` main" > /etc/apt/sources.list.d/gitlab_gitlab-ce.list
RUN wget -q -O - https://packages.gitlab.com/gpg.key | apt-key add -
RUN apt-get update && apt-get install -yq --no-install-recommends gitlab-ce

RUN mkdir -p /opt/gitlab/sv/sshd/supervise \
&& mkfifo /opt/gitlab/sv/sshd/supervise/ok \
&& printf "#!/bin/sh\nexec 2>&1\numask 077\nexec /usr/sbin/sshd -D" > /opt/gitlab/sv/sshd/run \
&& chmod a+x /opt/gitlab/sv/sshd/run \
&& ln -s /opt/gitlab/sv/sshd /opt/gitlab/service \
&& mkdir -p /var/run/sshd

RUN echo "UseDNS no" >> /etc/ssh/sshd_config
RUN echo "" && echo "# Docker options" && echo "# Prevent Postgres from trying to allocate 25% of total memory" && \
echo "postgresql['shared_buffers'] = '1MB'" >> /etc/gitlab/gitlab.rb \
&& mkdir -p /assets/ && cp /etc/gitlab/gitlab.rb /assets/gitlab.rb

EXPOSE 443 80 22

RUN (printf '#!/bin/bash\n\nset -e\n\n\
function sigterm_handler() {\n\techo "SIGTERM signal received, try to gracefully shutdown all services..."\n\tgitlab-ctl stop\n}\n\ntrap "sigterm_handler; exit" TERM\n\n/opt/gitlab/embedded/bin/runsvdir-start &\n\ngitlab-ctl reconfigure\n\ngitlab-ctl tail\n\n') \
> /usr/local/bin/wrapper && chmod +x /usr/local/bin/wrapper

RUN /etc/init.d/ssh stop

ENTRYPOINT ["/usr/local/bin/wrapper"]
