FROM debian
RUN apt-get update && apt-get --yes upgrade && apt-get --yes install curl && apt-get --yes install lbzip2
RUN mkdir ~/tsinstall
WORKDIR ~/tsinstall
RUN curl "http://dl.4players.de/ts/releases/3.1.1/teamspeak3-server_linux_amd64-3.1.1.tar.bz2" > tsinstall.tar.bz2 \
&& tar xf tsinstall.tar.bz2
WORKDIR ~/tsintall/teamspeak3-server_linux_amd64/
RUN export TS3SERVER_LICENSE=accept
EXPOSE 9987:9987
ENTRYPOINT ["/bin/bash", "-c", "ts3server_minimal_runscript.sh"
