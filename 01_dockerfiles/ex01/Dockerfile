#docker build -t ts3server .

#docker run -it -p 30033:30033 -p 9987:9987/udp -p 10011:10011 ts3server

FROM debian

RUN apt-get update -y && \
	apt-get upgrade -y && \
	apt-get install build-essential -y && \
	apt-get install curl -y && \
	apt-get install bzip2 -y

RUN useradd teamspeak

WORKDIR /home/teamspeak

RUN curl http://dl.4players.de/ts/releases/3.7.1/teamspeak3-server_linux_amd64-3.7.1.tar.bz2 > teamspeak_server.tar.bz2 && \
tar -xf teamspeak_server.tar.bz2

WORKDIR teamspeak3-server_linux_amd64

USER teamspeak

ENV TS3SERVER_LICENSE=accept

EXPOSE 9987/UDP
EXPOSE 30033
EXPOSE 10011

ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh"]
