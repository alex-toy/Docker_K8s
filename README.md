# Docker K8s

**IMPORTANT** : the *Dockerfile* is a "blueprint" for creating an image.

## Core Building Blocks

### Images

- create an image based on a *Dockerfile*
```
docker build .
docker build -t <my_image_name>:<my_tag> .
```

- rename image
```
docker image tag <image_id> <new_name>
```

- list images
```
docker images
```

- remove image
```
docker rmi <image_id>
```

- remove all unused images at once
```
docker image prune
```

- inspect image
```
docker image inspect <image_id>
```

### Containers
**IMPORTANT** : the command *docker run* creates a **new container** based on an **image**.

- create a container
```
docker run --name <custom_container_name> -p 3000:3000 <image_id>
```

**IMPORTANT** : **attach** mode means you receive output from the container in the console. You cannot provide input into the container.

- create a container in **detach** mode
```
docker run -d <image_id>
```

- attach to a container running in **detach** mode
```
docker attach <container_id>
```

**IMPORTANT** : **iteractive** mode means you can provide input to the container from the console.

- create a container in **iteractive** mode
```
docker run -it <image_id>
```

- create a container that is automatically removed when stopped
```
docker run --rm <image_id>
```

- start the container
```
docker start <container_id>
```

- start the container in **attach** mode
```
docker start -a <container_id>
```

- stop the container
```
docker stop <container_id>
```

- remove the container
```
docker rm <container_id>
```

- remove all stopped containers at once
```
docker container prune
```

- rename container
```
docker rename my_container my_new_container
```

- debug a running container
```
docker logs <container_id>
```

- copy folder to and from a container. 
**Note** : *inside_container_folder* is created if not existing
**Note** : container name should be followed by a semi column :
```
docker cp my_local_folfer/. my_container:/inside_container_folder
docker cp my_container:/inside_container_folder my_folfer
```


## External Storage

Volumes are folders on the host machine hard drive that are mounted (mapped) into containers. They connect a folder inside a container to a folder outside the container. A container can read / write data from a volume. Volumes persist if a container is dropped.

There are two types of external data storage :

- **Volumes** : managed by docker (docker sets up a path on the hosts machine, unknown to the developper).
- **Bind Mounts** : managed by developper.

### Data Categories

- **Application** : 
    - added to image at build phase
    - stored in images
    - read-only : can't be changed once image is built

- **Temporary App Data** : 
    - produced in running container
    - stored in containers (in memory or temporary files)
    - read-write (dynamic and changing, cleared regularly)
    - lost when container stops ???

- **Permanent App Data** : 
    - produced in running container
    - stored in files or in a database
    - read-write
    - not lost when container stops and even the removal of a container
    - stored using **volumes**

### Volumes

Volumes are great for data which should be persistent byt which you don't need to edit directly.

- list all volumes
```
docker volume ls
```

- remove volume
```
docker volume rm volume_id
```

- remove all unused volumes
```
docker volume prune
```

#### Anonymous Volumes
- created specifically for a single container -> cannot be shared accross containers

- **Always deleted when container is dropped**, but survives when container is stopped then restarted

- can be created in two ways :

    - inside Dockerfile with the **VOLUME** instruction.
    ```
    VOLUME ["/path/to/volume"]
    ```

    - in the run command
    ```
    docker run -v /path/to/volume image_id
    ```

#### Named Volumes
- not tied to a specific container -> used to share data accross containers

- **not deleted after the container is dropped** -> can be reused for the same container accross restarts

- created when running a container :
```
docker run -v volume_name:/app/path/to/volume image_id 
```

### Bind Mounts
They are great for persistent and editable data, for example the **source code**

- not tied to a specific container -> can be shared accross containers

- can be reused for the same container accross restarts

- created when running a container :
```
docker run -v "/path/to/source/code:/app" image_id 
```

- **IMPORTANT** : in order to not override files such as *node_modules*, you need to add an *anonymous volume* to *node_modules*
```
docker run -v "/path/to/source/code:/app" -v /path/to/node_modules image_id 
```

- shortcuts macOS / Linux: 
```
-v $(pwd):/app
```

- shortcuts windows
```
-v "%cd%":/app
```

- shortcuts powershell
```
-v ${pwd}:/app
```

## Networks
