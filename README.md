# Quick Wordpress Setup With Docker
install Wordpress locally using Docker Compose

## Video Tutorial (2019) by Traversy Media
https://youtu.be/pYhLEV-sRpY

## How to Install WordPress on Docker (2023)
https://www.hostinger.com/tutorials/run-docker-wordpress

To install Wordpress, 

1. Copy the `docker-compose.yaml` file from this repository to a local directory

2. Create a password file
```
echo "my_password" > "wordpress_password.txt"
```

3. Run docker-compose up in detached mode
```
docker-compose up -d
```

4. To remove the installed docker containers 
```
docker-compose down
```

### More commands
Create images and containers
> docker-compose up
 
Create images and containers in detached mode
> docker-compose up -d

Stop and delete all containers created by docker-compose
> docker-compose down

Delete all images created by docker-compose
> docker-compose down --rmi all

Delete all images and volumes created by docker-compose
> docker-compose down --rmi all --volumes

Delete all volumes created by docker-compose
> docker-compose down --volumes

## References
Docker Compose File
https://docs.docker.com/compose/compose-file/03-compose-file/

Net Ninja Docker Compose Tutorial
https://youtu.be/QePBbG5MoKk
