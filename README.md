# ECR-ECS-Integration
Creating Dockerfile for the web application and pushing the file to ECR private repo. So we can call the file using the ECS and run the task

ECS is a fully managed container orchestration service that allows you to run Docker containers at scale. It eliminates the need to manage your own container orchestration infrastructure and provides a highly scalable, reliable, and secure environment for deploying and managing your applications.

## ECS compared to other tools in the market

**Compared to Kubernetes:** Much less functionalities as compared to kubernetes , as it provides more granular control over the environment nad has better community as compared to ECS. So you can create controller for services that does not support containerization.

**Compared to Docker Swarm :** Docker Swarm is relatively easy to set up and is suitable for small to medium-scale deployments. However, as your application grows, ECS outshines Docker Swarm in terms of scalability, reliability, and seamless integration with AWS features like IAM roles and CloudWatch.

## ECS Core components : 

Clusters:
A cluster is a logical grouping of EC2 instances or Fargate tasks on which you run your containers. It acts as the foundation of ECS, where you can deploy your services.

Task Definitions:
Task Definitions define how your containers should run, including the Docker image to use, CPU and memory requirements, networking, and more. It is like a blueprint for your containers.

Tasks:
A task represents a single running instance of a task definition within a cluster. It could be a single container or multiple related containers that need to work together.

Services:
Services help you maintain a specified number of running tasks simultaneously, ensuring high availability and load balancing for your applications.

## ECS-ECR integration 

You can launch and EC2 instance and download AWS CLI and docker on it by using the following commands : 

`curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"` - downloading the package 

`unzip awscliv2.zip` - unzip the package

`sudo ./aws/install` - install aws cli 

`sudo snap install docker` - installing docker

Please make sure to configure the AWS CLI with access and secret access keys and create your private registry on ECR

### Create and Push the Dockerfile ###

`nano Dockerfile`

`sudo docker build -t 471112953589.dkr.ecr.ap-south-1.amazonaws.com/demo-repo:latest .` - name of the registry of ECR along with the tag

`sudo docker push 471112953589.dkr.ecr.ap-south-1.amazonaws.com/demo-repo:latest` - push the image

### Creating a Task Definition: ###
Define the task using the ECS CLI or the AWS Management Console.

### Configuring the Service: ###
Create an ECS service to manage the desired number of tasks and set up load balancing.

### Deploying the Service: ###
Use the ECS CLI or the AWS Management Console to deploy the service.

### Monitoring the Service: ###
Monitor your ECS service using AWS CloudWatch metrics and logs.


