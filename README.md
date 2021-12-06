# Docker Sponge

Docker sponge is a Minecraft server environment for [Sponge](https://www.spongepowered.org/) / [Forge](http://files.minecraftforge.net/) servers.

* Supports Sponge Forge

* Not meant for production environments

## Quick Setup

1. Install [Docker Toolbox](https://www.docker.com/products/docker-toolbox) or [Docker Desktop](https://www.docker.com/products/docker-desktop) or [Docker Engine](https://docs.docker.com/engine/install/)

3. Clone project:

    ```
    $ git clone git@github.com:opencoca/minecraft-docker.git  
    $ cd minecraft-docker/
    ```  
    
4. Run the setup
        
    * Create Sponge Forge:
    
        ```
        $ sponge-forge/setup.sh
        ```
    
5. Browse and update your Mincraft server files in the following locations:

    * `./sponge-forge/data`

    
### Customizing Quick Setup

1. Edit the `docker-compose.yml` in the root of the project.

    * You can update the following settings:
    
        * Container Name
        
        * Port(s)
        
        * Sponge and Forge Versions
        
        * Memory

2. You may add additional ports by adding to the `ports:` and `expose:` sections.

3. If you already have a running container you can destroy it:

    ```
    $ docker stop forge  
    $ docker rm forge
    ```
    
    
4. (Re)build your container:  

    * Sponge Forge:  
    
        ```
        $ cd sponge-forge/  
        $ docker-compose up -d
        ```


## Manual Setup

1. Install [Docker Toolbox](https://www.docker.com/products/docker-toolbox) or [Docker Desktop](https://www.docker.com/products/docker-desktop) or [Docker Engine](https://docs.docker.com/engine/install/)

3. Create container(s):
    
    **Sponge Forge**
    ```
    $ docker run -itd -p 25566:25566 \
    -v /path/on/host:/forge \
    -e MINECRAFT_PORT=25566 \
    -e MINECRAFT_EULA=true \
    -e MINECRAFT_MAXHEAP=1024M \
    -e FORGE_VERSION=1.8.9-11.15.1.1890-1.8.9 \
    -e SPONGE_VERSION=1.8.9-1890-4.2.0-BETA-1446 \
    --name forge openco/sponge-forge
    ```
    

* Minecraft server files will be placed in the path you specified on this line `-v /path/on/host:/forge`

    * On Windows, the host path should start from `//c/Users/<path>`

    * On Mac, the host path should start from `/Users/<path>`

* You may add additional ports by adding `-p XXXX:XXXX --expose XXXX` (change `XXXX` to the desired port number)


## Attaching to the running containers:

```
**Mac/Linux:**   

```
$ docker attach forge  
$ docker attach vanilla
```

## Detaching from the running containers:

Keystroke: `[CTRL]` + `[p]` then `[CTRL]` + `[q]`

**NOTE**: If you `[CTRL]` + `[c]` while attached to the running container, the container will be stopped.

## Starting and stopping the server

```
$ docker stop forge  
$ docker start forge
```  

