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

- copy folder to and from a container. 
**Note** : *inside_container_folder* is created if not existing
**Note** : container name should be followed by a semi column :
```
docker cp my_local_folfer/. my_container:/inside_container_folder
docker cp my_container:/inside_container_folder my_folfer
```


## Volumes

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


## Networks
