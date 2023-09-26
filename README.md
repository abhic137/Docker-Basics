# Docker-Basics
Install docker in your system.

### Pulling and using an ubuntu image
```
sudo docker pull ubuntu
```

### Checking the downloaded image
```
sudo docker images
```

### running the downloaded image

```
sudo docker run --name <IMAGE_NAME> -id ubuntu
```

### to check if the docker is running
```
sudo docker ps -a
```

### to get into the docker
```
sudo docker exec -it <NAME_OF_THE_IMAGE>bash
```
### To kill or stop the docker
```
sudo docker kill <IMAGE_NAME>
```

### To remove the presence
```
sudo docker rm <IMAGE_NAME>
```
