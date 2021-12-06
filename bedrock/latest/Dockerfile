FROM fedora:latest
RUN yum install -y wget
RUN yum install -y unzip 
RUN yum install -y libnsl
VOLUME ["/data"]
RUN wget 'https://minecraft.azureedge.net/bin-linux/bedrock-server-1.18.1.02.zip'
RUN unzip bedrock*
EXPOSE 19132
RUN chmod +x ../bedrock_server
CMD sed -i 's/allow-cheats=false/allow-cheats=true/g' ../server.properties && LD_LIBRARY_PATH=. ../bedrock_server
WORKDIR /data 
