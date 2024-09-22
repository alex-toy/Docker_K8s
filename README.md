# Docker K8s

## Useful commands

### Images

- create an image based on a *Dockerfile*
```
docker build .
docker build -t <my_image_name> .
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

### Containers
**IMPORTANT** : the command *docker run* creates a **new container** based on an **image**.

- create a container
```
docker run --name <custom_container_name> -p 3000:3000 <image_id>
```

**IMPORTANT** : **attach** mode means you receive output from the container in the console. You cannot provide input into the container.

- create a container in **detach** mode
```
docker run *-d* <image_id>
```

- attach to a container running in **detach** mode
```
docker attach <container_id>
```

**IMPORTANT** : **iteractive** mode means you can provide input to the container from the console.

- create a container in **iteractive** mode
```
docker run *-it* <image_id>
```

- create a container that is automatically removed when stopped
```
docker run *--rm* <image_id>
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
