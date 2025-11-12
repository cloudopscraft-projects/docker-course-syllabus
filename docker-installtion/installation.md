# 🐳 Quick Docker Installation on Ubuntu

Run the following commands to install **Docker Engine**, **Docker CLI**, **Buildx**, and **Docker Compose plugin**:

```bash
# Update packages
sudo apt-get update

# Install dependencies
sudo apt-get install -y ca-certificates curl gnupg lsb-release

# Add Docker GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# Add Docker repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update package index
sudo apt-get update

# Install Docker and plugins
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Optional: run Docker without sudo
sudo usermod -aG docker $USER
newgrp docker

# Verify installation
docker --version
docker compose version
docker run hello-world


---

This version is **easy for beginners** — they can copy the entire block into their terminal and follow along.  

If you want, I can also make an **even shorter “one-liner install command”** that runs everything automatically. Do you want me to do that too?
