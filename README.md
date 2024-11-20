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
sudo apt update -y && sudo apt upgrade -y
sudo apt  install awscli
aws configure
sudo apt install -y apt-transport-https ca-certificates curl software-properties-common
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io
docker --version
sudo systemctl status docker
```
```
# create ECR with name: my-flask-app
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 866824485776.dkr.ecr.us-east-1.amazonaws.com
```
