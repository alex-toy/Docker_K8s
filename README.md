# Docker K8s


## Getting Started

### Node App

- cd into *node_app*

- run 
```
docker build .
docker build -t <my_image_name> .
```

- get the image id

- run 
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




