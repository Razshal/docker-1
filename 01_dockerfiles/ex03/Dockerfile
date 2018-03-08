FROM ubuntu:14.04

RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates openssh-server wget apt-transport-https
RUN echo "deb https://packages.gitlab.com/gitlab/gitlab-ce/ubuntu/ `lsb_release -cs` main" > /etc/apt/sources.list.d/gitlab_gitlab-ce.list
RUN wget -q -O - https://packages.gitlab.com/gpg.key | apt-key add -
RUN apt-get update && apt-get install -yq --no-install-recommends gitlab-ce

RUN (printf '#!/bin/bash\n\nset -e\n\n\
function sigterm_handler() {\n\techo "SIGTERM signal received, try to gracefully shutdown all services..."\n\tgitlab-ctl stop\n}\n\ntrap "sigterm_handler; exit" TERM\n\n/opt/gitlab/embedded/bin/runsvdir-start &\n\ngitlab-ctl reconfigure\n\ngitlab-ctl tail\n\n') \
> /usr/local/bin/wrapper && chmod +x /usr/local/bin/wrapper

EXPOSE 443 80 22
ENTRYPOINT ["/usr/local/bin/wrapper"]
