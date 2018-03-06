FROM debian

RUN apt-get update && apt-get install -y --no-install-recommends vim wget gcc zsh git unzip ca-certificates default-jre default-jdk
RUN mkdir /install
RUN git clone https://github.com/Razshal/myVim.git && mv myVim/.vim* ~/ && rm -rf myVim
WORKDIR /usr/local
RUN wget http://mcmyadmin.com/Downloads/etc.zip && unzip etc.zip && rm etc.zip
RUN adduser minecraft && su minecraft
RUN cd /home/minecraft && mkdir McMyAdmin
WORKDIR /home/minecraft/McMyAdmin
RUN wget http://mcmyadmin.com/Downloads/MCMA2_glibc26_2.zip
RUN unzip MCMA2_glibc26_2.zip && rm MCMA2_glibc26_2.zip
RUN ./MCMA2_Linux_x86_64 -setpass password -nonotice

EXPOSE 8080/tcp
EXPOSE 25565/tcp
