🐳 Docker Installation on Ubuntu

Follow the steps below to install Docker Engine, Docker CLI, Buildx, and Docker Compose plugin on Ubuntu.

1️⃣ Update your system
sudo apt-get update

2️⃣ Install required dependencies
sudo apt-get install ca-certificates curl gnupg lsb-release -y

3️⃣ Add Docker’s official GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

4️⃣ Set up the Docker repository
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

5️⃣ Update package index again
sudo apt-get update

6️⃣ Install Docker Engine and components
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

7️⃣ Verify Docker installation
docker --version
docker compose version


✅ Optional: To run Docker without sudo, add your user to the Docker group:

sudo usermod -aG docker $USER
newgrp docker


Then verify:

docker run hello-world

📦 Installed Components
Component	Description
docker-ce	Docker Engine (Community Edition)
docker-ce-cli	Command line interface for Docker
containerd.io	Container runtime
docker-buildx-plugin	Extended build capabilities (BuildKit)
docker-compose-plugin	Compose v2 plugin (docker compose)
