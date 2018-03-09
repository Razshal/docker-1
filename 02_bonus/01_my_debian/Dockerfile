FROM debian

RUN apt-get update && apt-get upgrade -y && apt-get install -y --no-install-recommends zsh vim gcc curl wget git ca-certificates
RUN git config --global user.email "fontenille.mathieu@gmail.com"
RUN git config --global user.name "Razshal"
RUN if ! sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"; then echo error during oh my zsh install; fi
RUN git clone https://github.com/Razshal/myWorkEnv.git /tmp/envinstall
WORKDIR /tmp/envinstall
RUN sh install.sh
RUN cp .zshrc $HOME/
WORKDIR /root
RUN rm -rf /tmp/envinstall
ENTRYPOINT ["zsh"]
