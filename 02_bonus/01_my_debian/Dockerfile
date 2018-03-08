FROM debian

RUN apt-get update && apt-get install -y --no-install-recommends zsh vim gcc curl git ca-certificates
WORKDIR /tmp
RUN git clone https://github.com/Razshal/myWorkEnv.git envinstall
RUN sh /tmp/envinstall/install.sh
RUN sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
