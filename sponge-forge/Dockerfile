FROM java:8

LABEL MAINTAINER OpenCo (OpenCoCA on Github)

ENV MINECRAFT_PORT 25565
ENV MINECRAFT_EULA true
ENV MINECRAFT_MAXHEAP 2048M

ENV FORGE_VERSION 1.12.2-14.23.5.2855
ENV FORGE_URL https://files.minecraftforge.net/maven/net/minecraftforge/forge/${FORGE_VERSION}/forge-${FORGE_VERSION}-installer.jar

ENV SPONGE_VERSION 1.12.2-2838-7.3.0
ENV SPONGE_URL https://files.minecraftforge.net/maven/org/spongepowered/spongeforge/${SPONGE_VERSION}/spongeforge-${SPONGE_VERSION}.jar

ENV EXECUTABLE_JAR forge-${FORGE_VERSION}.jar

RUN DEBIAN_FRONTEND=noninteractive
RUN apt-get install ca-certificates

VOLUME ["/forge"]

ADD ./scripts/start.sh /start_forge
RUN chmod +x /start_forge

EXPOSE ${MINECRAFT_PORT}
CMD ["/start_forge"]
#For debugging instead leave the container running
#CMD exec /bin/bash -c "trap : TERM INT; sleep infinity & wait"
