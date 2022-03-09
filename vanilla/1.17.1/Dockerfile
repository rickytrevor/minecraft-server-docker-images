FROM ubuntu as installer 
RUN apt -y update
RUN apt -y install curl tar

ARG RCON_CLI_VER=1.4.8
ADD https://github.com/itzg/rcon-cli/releases/download/${RCON_CLI_VER}/rcon-cli_${RCON_CLI_VER}_linux_amd64.tar.gz /tmp/rcon-cli.tgz
RUN tar -x -C /usr/local/bin -f /tmp/rcon-cli.tgz rcon-cli && \
  rm /tmp/rcon-cli.tgz
VOLUME ["/data"]
EXPOSE 25565/tcp
EXPOSE 25565/udp
FROM alpine:latest
COPY --from=installer /usr/local/bin /usr/local/bin
RUN apk update 
RUN apk add openjdk17  
#RUN apk add bash
RUN echo "sed -i 's/enable-rcon=false/enable-rcon=true/g' server.properties && sed -i 's/server-ip=/server-ip=0.0.0.0/g' server.properties && sed -i 's/rcon.password=/rcon.password=mc/g'  server.properties" > activateconsole.sh 
RUN printf "if [ ! -f server.jar ]; then echo 'server.jar not found, downloading...'\n apk update && apk add wget && wget https://launcher.mojang.com/v1/objects/0a269b5f2c5b93b1712d0f5dc43b6182b9ab254e/server.jar -O server.jar \nfi\n echo 'eula=true' > eula.txt\n cp ../activateconsole.sh . \njava -jar server.jar " > download.sh
RUN chmod +x download.sh
CMD cp ../download.sh . &&  sh download.sh
WORKDIR /data