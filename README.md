# minecraft-server-docker-images
This repository is ment to contain a lot of docker images to run various versions minecraft servers, with time i'll add more versions and if you have any issues feel free to 
open an issue on github and i'll fix it as soon as possible

#### Supported editions:
Bedrock, Vanilla, Spigot, Forge (if you plan to run the Bedrock version remember to use /udp after the port -p 19132:19132/udp) 
https://hub.docker.com/repository/docker/rickytrevor/minecraft-server

##### Usage:

```
docker run --rm --name mcserver -v /the/directory/that/you/want:/data -p 25565:25565 -t -d rickytrevor/minecraft-server:vanilla-latest
```

if you want to run a specific minecraft version add after the : the version number

#### example:

```
docker run --rm --name mcserver -v /the/directory/that/you/want:/data  -p 25565:25565  -t -d rickytrevor/vminecraft-server:1.16.5
```

#### console:

you can access the minecraft server console by going inside the directory that you've specified after the -v there's a shell script called "activateconsole.sh", by running it it'll enable the console and then to access it just run (make sure YOUR USER has the permition to write on the server.properties config file, otherwise you won't be able to activate the console)

```
docker exec -i nameofyourcontainer rcon-cli --host localhost --port 25575 --password mc
```

To install plugins you have to run the spigot version and then you place them in the plugins folder

have fun :D


#### other projects that i've used to create those docker images

[GitHub - itzg/rcon-cli: A little RCON cli based on james4k&#39;s RCON library for golang](https://github.com/itzg/rcon-cli)
