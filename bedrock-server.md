# Container
https://github.com/itzg/docker-minecraft-bedrock-server

# Install the container
```sh
docker run -d -it --name bedrock-server -e EULA=TRUE -e GAMEMODE=survival -p 19132:19132/udp -v bedrock:/data --user 1000:1000 itzg/minecraft-bedrock-server

```
> -d runs the container in detached mode.
>
> -it allows for interactive terminal mode, which is generally helpful for attaching if needed.
>
> --name bedrock-server names the container.
>
> -e EULA=TRUE sets the EULA to true.
>
> -p 19132:19132/udp maps the necessary port.
>
> -v mc-bedrock-data:/data mounts the volume mc-bedrock-data to persist server data.

# container commands
```sh
# Start the server: 
docker start bedrock-server

# Stop the server: 
docker stop bedrock-server

# restart server
docker restart bedrock-server

# View logs: 
docker logs -f bedrock-server
```

# Access the properties
```sh
cd mc-bedrock-data/
nano server.properties
```

# list all running containers
```sh
docker ps -a
```

# Access the container shell
```sh
docker exec -it bedrock-server /bin/sh
# exit command to leave
```

# Remove the container
```sh
docker rm bedrock-server
```
# clear logs
```sh
# for container ID f49ba7632d944a0a634477eed577feaa85b13aa18261541878e923e6deafe4de

truncate -s 0 /var/lib/docker/containers/f49ba7632d944a0a634477eed577feaa85b13aa18261541878e923e6deafe4de/f49ba7632d944a0a634477eed577feaa85b13aa18261541878e923e6deafe4de-json.log

``

# minecraft commands 
```sh
docker attach bedrock-server


# say test

# https://minecraftbedrock-archive.fandom.com/wiki/Commands/List_of_Commands

# make operator 
op "MorganBratt"

# show coordinates
gamerule showcoordinates true

```

# update teh server files detailed
```sh
# create temp container to access the volume
docker run --rm -it -v bedrock:/data alpine /bin/sh

apk update
apk add nano

# edit and save settings
nano /data/server.properties

docker restart bedrock-server
```

# Set the container to run on start
```sh

# verify the status
docker inspect -f '{{ .HostConfig.RestartPolicy.Name }}' bedrock-server

# update
docker update --restart unless-stopped bedrock-server

# verify the status
docker inspect -f '{{ .HostConfig.RestartPolicy.Name }}' bedrock-server



```