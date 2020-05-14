FROM debian

### Env
ENV TS3SERVER_LICENSE=accept

WORKDIR /home/teamspeak/

EXPOSE 9987/udp 10011 30033

RUN apt-get update && apt-get upgrade -y && apt-get install -y wget bzip2
RUN wget http://dl.4players.de/ts/releases/3.12.1/teamspeak3-server_linux_amd64-3.12.1.tar.bz2
RUN tar xvf *.tar.bz2

RUN cd teamspeak3-server_linux_amd64 && mv * /home/teamspeak && cd .. && rm -f teamspeak3-server_linux_amd64-3.12.1.tar.bz2
###RUN touch /home/teamspeak/.ts3server_license_accepted  && chmod 777 /home/teamspeak/.ts3server_license_accepted

### Starting
###CMD su teamspeak -c "/home/teamspeak/ts3server_startscript.sh start"
CMD  sh /home/teamspeak/ts3server_minimal_runscript.sh

