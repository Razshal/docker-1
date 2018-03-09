FROM ubuntu:16.04

RUN apt-get update && apt-get upgrade -y && apt-get install -y --no-install-recommends \
openvpn curl iptables apt-utils ca-certificates openssl
WORKDIR /tmp
RUN curl http://swupdate.openvpn.org/as/openvpn-as-2.5-Ubuntu16.amd_64.deb > openvpninstall.deb
RUN bash -c 'echo -e "yes\nyes\n1\n943\n443\nyes\nyes\nyes\nyes\nyes\n"' | dpkg -i openvpninstall.deb
RUN bash -c 'echo -e "default\ndefault"' | passwd openvpn

EXPOSE 943/tcp 443/tcp
