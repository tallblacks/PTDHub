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


