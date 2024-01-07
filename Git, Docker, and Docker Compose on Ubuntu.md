#### Install Git ####
```shell
sudo apt update
sudo apt install git

// View the list of upgradeable software
sudo apt list --upgradable
// Upgrade
sudo apt upgrade
```

#### Install Docker ####
1. Update package index
```shell
sudo apt update
```
2. Install necessary dependencies for Docker
```shell
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
```
3. Add Docker's official GPG key. Docker uses GPG keys to sign its packages to ensure the integrity and authenticity of the software. In this step, download Docker's GPG key and add it to the system keyring.
```shell
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
4. Set up Docker's software source repository
```shell
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
5. Update the package index
```shell
sudo apt update
```
6. Install Docker
```shell
sudo apt install docker-ce docker-ce-cli containerd.io
```
7. Verify Docker installation
```shell
sudo docker --version
```

#### Install Docker Compose ####
1. Download the Docker Compose binary
```shell
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
2. Add execute permissions
```shell
sudo chmod +x /usr/local/bin/docker-compose
```
3. Verify Docker Compose installation
```shell
docker-compose --version
```

#### Common Docker Commands ####
View All Containers (Including Stopped Ones)
```shell
docker ps -a
```
View Container Logs
```shell
docker logs nzshop-container
```
Enter Container
```shell
docker exec -it <container_id_or_name> /bin/bash
docker exec -it $(docker-compose ps -q <service-name>) /bin/bash
```
Docker Network
```shell
docker network ls
docker network create nzshop-network
docker network connect nzshop-network <container_id_or_name_1>
docker network connect nzshop-network <container_id_or_name_2>
# Delete All Unused Docker Networks
docker network prune -f 
```
Images and Volumes
```shell
# Force Delete All Local Images
docker rmi -f $(docker images -aq) 
# Delete All Unused Docker Volumes
docker volume prune -f 
```
Push to Docker Hub
```shell
docker push topstory/nzshop-web:1.0
```
Start, Stop, and Remove Containers
```shell
docker stop <container_name_or_id>
docker stop $(docker ps -aq)
docker start <container_id_or_name>
docker rm <container_id_or_name>
docker rm $(docker ps -aq)
```
Clean Docker Cache
```shell
docker system prune -a
```
Delete Built Docker Images
```shell
docker rmi IMAGE_ID
docker rmi $(docker images -q)
```

#### Common Docker-Compose Commands ####
Build and Run
```shell
docker-compose build
docker-compose up -d
```
Start services, rebuild images, and run in the background using Docker Compose
```shell
docker-compose up --build -d
```
Retrieve the ID of the container
```shell
docker-compose ps -q <service-name>
```
Stop and Remove all services, networks, and containers defined in the `docker-compose.yml` file.
```shell
docker-compose down
```
Stop and remove all services, networks, and containers defined in Docker Compose, while also deleting associated volumes. 
This command is crucial when changing databases or updating database versions.
```shell
docker-compose down -v
```
Just stop the services without removing them
```shell
docker-compose stop
```
Logs
```shell
docker-compose logs
```


