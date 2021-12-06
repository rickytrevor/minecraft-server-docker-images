FROM ubuntu 
RUN apt -y update
RUN apt -y install wget
RUN apt -y install unzip 
VOLUME ["/data"]
RUN wget 'https://minecraft.azureedge.net/bin-linux/bedrock-server-1.18.1.02.zip'
RUN unzip bedrock*
EXPOSE 19132
RUN chmod +x ../bedrock_server
CMD sed -i 's/allow-cheats=false/allow-cheats=true/g' ../server.properties && LD_LIBRARY_PATH=. ../bedrock_server
WORKDIR /data 
