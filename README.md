When we deploy keycloak in any cluster, if we access it and try to do log in it will give erro "https required".So use keycloak.yml file which is present in this repo and deploy it in any cluster and do login it will not give error along with if we want to add any volume or any confguraion, we can do as it is.


JENKINS-EKS INTEGRATION
=========================
We donot need any plugin to install to connect to eks cluster.We onle need to install aws cli,configure it by providing appropritae iam use access_key,secret_access_key and install kubectl command.After that update the kubeconfig file of the cluster. Then use the Jenkinsfile present in this repo to connect to eks and execute kubectl commands to deploy application.

COMMANDS
=========

# Install AWS CLI v2
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
sudo apt install unzip
unzip awscliv2.zip
sudo ./aws/install -i /usr/local/aws-cli -b /usr/local/bin --update

# Setup your access by


aws configure


# Install Docker(NO NEED IF ALREADY INSTALLED)

sudo apt-get update
sudo apt install docker.io -y
docker ps
sudo chown $USER /var/run/docker.sock

# Install kubectl

curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin
kubectl version --short --client



# Install eksctl

curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version

# UPDATE KUBECONFIGFILE


aws eks update-kubeconfig --region us-west-2 --name <name>
kubectl get nodes
