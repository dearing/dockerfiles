# Minecraft 1.7.10 with eula.txt agreement
# ex. docker run -name minecraft -dti -p 25565:25565
# ex. docker attach minecraft
FROM ubuntu:latest
MAINTAINER Jacob Dearing <jacob.dearing@gmail.com>

# UPDATE our systems and install junk we need to party
RUN apt-get update && apt-get upgrade -y && apt-get install -y wget nano default-jre-headless
RUN mkdir /srv/minecraft
RUN useradd -rMs /bin/false minecraft

# SETUP our server with the defaults at the Dockerfile
WORKDIR /srv/minecraft
RUN wget --no-check-certificate -O minecraft.jar https://s3.amazonaws.com/Minecraft.Download/versions/1.7.10/minecraft_server.1.7.10.jar
ADD defaults /srv/minecraft
RUN chown minecraft:minecraft -R /srv/minecraft

# 25565 is the default needed to play, edit accordingly
EXPOSE 25565
USER minecraft
CMD ["java", "-jar", "minecraft.jar", "nogui", "-Xmx1024M", "Xms1024M"]
