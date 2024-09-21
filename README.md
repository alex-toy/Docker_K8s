# Docker K8s

## Useful commands

### Images

- create an image based on a *Dockerfile*
```
docker build .
docker build -t <my_image_name> .
```

- list images
```
docker images
```

- remove image
```
docker rmi <image_id>
```

### Containers
**IMPORTANT** : the command *docker run* creates a **new container** based on an **image**.

- create a container
```
docker run --name <custom_container_name> -p 3000:3000 <image_id>
```

- create a container in **detach** mode
```
docker run --name <custom_container_name> -d -p 3000:3000 <image_id>
```

- attach a container in **detach** mode
```
docker attach <container_id>
```

- stop the container
```
docker stop <container_id>
```

- remove the container
```
docker rm <container_id>
```


## Node Project

### Node App

- cd into *node_app*

- create an image based on a *Dockerfile*
```
docker build .
docker build -t <my_image_name> .
```

- get the image id

- **IMPORTANT** : the command *docker run* creates a **new container** based on an **image**
```
docker run -p 3000:3000 <image_id>
docker run --name <custom_container_name> -p 3000:3000 <image_id>
```

- visit http://localhost:3000. The container is now running a web app.

- get the id of the container
```
docker ps
```

- stop the container
```
docker stop <container_id>
```

- remove the container
```
docker rm <container_id>
```




