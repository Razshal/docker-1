FROM debian
RUN apt-get update && apt-get --yes upgrade && apt-get --yes install curl && apt-get --yes install lbzip2
RUN mkdir /root/tsinstall
WORKDIR /root/tsinstall
RUN curl "http://dl.4players.de/ts/releases/3.0.13.8/teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2" > tsinstall.tar.bz2 \
&& tar xf tsinstall.tar.bz2
WORKDIR teamspeak3-server_linux_amd64/
RUN touch .ts3server_license_accepted
EXPOSE 9987:9987/udp
EXPOSE 30033:30033/tcp
ENTRYPOINT ["./ts3server_minimal_runscript.sh"]
