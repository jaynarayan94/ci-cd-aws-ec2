# ci-cd-python - Commands to install Docker on EC2 
- Ensure port 80 is available
```
sudo yum update -y
sudo amazon-linux-extras install docker
sudo service docker start
sudo systemctl start docker
sudo service docker status
sudo groupadd docker
sudo usermod -a -G docker ec2-user
newgrp docker
docker —-version
```

```
[Ubuntu Machine]
# Update the package index
sudo apt-get update -y

# Install required packages for Docker installation
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

# Add Docker's official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add the Docker repository to APT sources
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update the package index again to include Docker packages
sudo apt-get update -y

# Install Docker
sudo apt-get install -y docker-ce docker-ce-cli containerd.io

# Start the Docker service
sudo systemctl start docker

# Enable Docker to start on boot
sudo systemctl enable docker

# Check Docker service status
sudo systemctl status docker

# Create the docker group if it doesn't exist
sudo groupadd docker

# Add your user to the docker group
sudo usermod -aG docker $USER

# Refresh group membership without logging out
newgrp docker

# Verify Docker installation
docker --version

# Test Docker by running a simple container
docker run hello-world

```
```
aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
aws-region: ${{ secrets.AWS_REGION }}
${{ secrets.AWS_ACCOUNT_ID}} # AWS_ACCOUNT_ID : Aws login Account id
${{ secrets.EC2_HOST }}  # Public IPv4 DNS
${{ secrets.EC2_USERNAME }}  # ec2-user or ubuntu
${{ secrets.EC2_SSH_KEY }}   #.pem file content/create key_pair for the ec2
```
