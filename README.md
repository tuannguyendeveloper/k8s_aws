<p align="center">
  <a href="https://kubernetes.io/" target="blank"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/39/Kubernetes_logo_without_workmark.svg/2109px-Kubernetes_logo_without_workmark.svg.png" width="200" alt="Nest Logo" /></a>
</p>

  <p align="center">Testing <a href="https://kubernetes.io/" target="_blank">Kubernetes</a> use  <a href="https://aws.amazon.com/eks/?nc1=h_ls" target="_blank">EKS</a> .</p>
    <p align="center">

## Architecture
<p align="center">
<img src=".\architecture\K8s_Architecture.png" width="800"/>
</p>

  - [Route53](https://aws.amazon.com/route53/) A reliable and cost-effective way to route end users to Internet applications. </br>
  - [WAF](https://aws.amazon.com/waf/) Protect your web applications from common exploits. </br>
  - [ELB](https://aws.amazon.com/elasticloadbalancing/) Distribute network traffic to improve application scalability. </br>
  - [Kong](https://docs.konghq.com/) Kong Enterprise is the fastest, most feature-advanced, and secure API management solution. </br>
  - [EKS](https://aws.amazon.com/eks/?nc1=h_ls) The most trusted way to start, run, and scale Kubernetes. </br>
  - [EC2](https://aws.amazon.com/ec2/?nc1=h_ls) Secure and resizable compute capacity for virtually any workload. </br>
  - [CloudWatch](https://aws.amazon.com/cloudwatch/) Observe and monitor resources and applications on AWS, on premises, and on other clouds. </br>
  - [Redis](https://redis.io/) Redis is an open source (BSD licensed), in-memory data structure store, used as a database, cache, and message broker. </br>
  - [NATS](https://nats.io/) The NATS Adaptive Edge Architecture allows for a perfect fit for unique needs to connect devices, edge, cloud or hybrid deployments. </br>
  - [Lens](https://k8slens.dev/) Lens IDE for Kubernetes. The only system you'll ever need to take control of your Kubernetes clusters. It's open source and free. </br>

## Structure folder
- Architecture - Include architecture image and draw.io file
- Nats - Include deployment and service config for nats
- Redis - Include deployment and service config for redis

## Installation
### Setup kubernetes cluster for linux
```bash
# Download file
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.18.8/2020-09-18/bin/linux/amd64/kubectl

# Set permission
chmod +x ./kubectl

# Move file
sudo mv ./kubectl /usr/local/bin
```

### Install the AWS CLI
```bash
# Download file & install
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg" sudo installer -pkg AWSCLIV2.pkg -target /
```

### Configure your AWS CLI credentials
```bash
# Update config aws-cli with access_key, secret_key
aws configure
```

### Install eksctl
```bash
# Download file
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

# Move file
mv /tmp/eksctl /usr/local/bin
```

### Create Kubernetes cluster
```bash
# Download file
eksctl create cluster --name=x --nodes=y --node-type z
```
- x - Cluster name
- y - Number of node
- z - instance type (ex: t3.micro, m5.large, ...)

### Cluster deployment
```bash
# Deploy nats service
kubectl apply -f nats/

# Deploy redis service
kubectl apply -f redis/
```
