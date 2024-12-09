
#### **Image Management**

Pull an image from a registry:

```sh
  docker pull ubuntu
```

Build an image from a Dockerfile:

```sh
  docker build -t my_image .
```

List images:

```sh
  docker images
```

Remove an image:

```sh
  docker rmi my_image
```

Remove all images:

```sh
  docker rmi $(docker images -q)
```


#### **Container Lifecycle**

Run a new container:

```sh
  docker run -d --name my_container nginx
```

Start a stopped container:

```sh
  docker start my_container
```

Stop a running container:

```sh
  docker stop my_container
```

Remove a container:

```sh
  docker rm my_container
```

Remove all containers:

```sh
  docker rm $(docker ps -a -q)
```


#### **Container Monitoring**

List containers:

```sh
  docker ps
```

Fetch the logs of a container:

```sh
  docker logs my_container
```

#### **Networking**

List networks:

```sh
  docker network ls
```

Create a new network:

```sh
  docker network create my_network
```

#### **Volumes**

List volumes:

```sh
  docker volume ls
```

Create a volume:

```sh
  docker volume create my_volume
```

If you need more examples or have any other questions, feel free to ask!