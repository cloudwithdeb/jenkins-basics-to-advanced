## Introduction To Jenkins

Jenkins is a Continues Integration and Continues Delivery Tool. It is one of the oldest CICD pipeline tools out ther being used by many people in the industry. Other CICD tools out ther include the following:

* Azure DevOps Yaml Pipelines
* Github Actions
* Circle CI
* Bamboo
* Octopus

## Setup Jenkins

There are several ways of installing jenkins but from their official documentation, they require you to use `Docker`. [Click to visit official documentation](https://www.jenkins.io/doc/book/installing/docker/).

### Setup on Linux / Mac Os using docker

#### Setp 1:
```bash
#1. Set Environment Variables
export IMAGE_NAME=''

#2. Build Docker image
docker image build -t $IMAGE_NAME .

#3. Create docker network
docker network create jenkins

#4. Deploy jenkins container
docker run --name jenkins-blueocean --restart=on-failure --detach \
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  cloudwithdeb/myjenkins:v1


#5. Use this command to display the Jenkins Password
docker exec jenkins-blueocean cat /var/jenkins_home/secrets/initialAdminPassword

```

### Setup on Windows using docker

```bash
#1. Build Docker image
docker image build -t cloudwithdeb/myjenkins:v1 .

#2. Create docker network
docker network create jenkins

#3. Deploy jenkins container
docker run --name jenkins-blueocean --restart=on-failure --detach `
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 `
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 `
  --volume jenkins-data:/var/jenkins_home `
  --volume jenkins-docker-certs:/certs/client:ro `
  --publish 8080:8080 --publish 50000:50000 cloudwithdeb/myjenkins:v1

#4. Use this command to display the Jenkins Password
docker exec jenkins-blueocean cat /var/jenkins_home/secrets/initialAdminPassword

```
