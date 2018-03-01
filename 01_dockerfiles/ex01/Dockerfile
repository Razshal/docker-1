FROM debian
RUN apt-get update && apt-get upgrade -y --force-yes && apt-get install curl -y --force-yes && apt-get install lbzip2 -y --force-yes
RUN mkdir ~/tsinstall
WORKDIR ~/tsinstall
RUN curl "http://dl.4players.de/ts/releases/3.1.1/teamspeak3-server_linux_amd64-3.1.1.tar.bz2" > tsinstall.tar.bz2 \
&& tar xf tsinstall.tar.bz2
WORKDIR ~/tsintall/teamspeak3-server_linux_amd64/
RUN export TS3SERVER_LICENSE=accept
