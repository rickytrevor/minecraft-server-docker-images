from fedora:latest
#RUN yum install -y java-1.8.0-openjdk.x86_64
RUN yum install -y java-latest-openjdk 
RUN yum install -y wget
RUN yum install -y shadow-utils
RUN yum install -y tar
RUN yum install -y git 
ARG RCON_CLI_VER=1.4.8
ADD https://github.com/itzg/rcon-cli/releases/download/${RCON_CLI_VER}/rcon-cli_${RCON_CLI_VER}_linux_amd64.tar.gz /tmp/rcon-cli.tgz
RUN tar -x -C /usr/local/bin -f /tmp/rcon-cli.tgz rcon-cli && \
  rm /tmp/rcon-cli.tgz
VOLUME ["/data"]
EXPOSE 25565/tcp
EXPOSE 25565/udp
RUN wget 'https://launcher.mojang.com/v1/objects/0a269b5f2c5b93b1712d0f5dc43b6182b9ab254e/server.jar'
RUN touch /data/eula.txt
RUN echo eula=true > /data/eula.txt
RUN echo "sed -i 's/enable-rcon=false/enable-rcon=true/g' server.properties && sed -i 's/server-ip=/server-ip=0.0.0.0/g' server.properties && sed -i 's/rcon.password=/rcon.password=mc/g'  server.properties" > activateconsole.sh 
CMD cp ../activateconsole.sh /data && echo eula=true > eula.txt && java -jar ../*.jar
WORKDIR /data
#docker exec -i mcserver rcon-cli --host localhost --port 25575 --password glaspalast timings report
