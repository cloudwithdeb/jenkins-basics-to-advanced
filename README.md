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
docker run --name jenkins-blueocean --restart=on-failure --detach \
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  myjenkins-blueocean:2.332.3-1

  ### Setup on Windows using docker

  docker run --name jenkins-blueocean --restart=on-failure --detach `
  --network jenkins --env DOCKER_HOST=tcp://docker:2376 `
  --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 `
  --volume jenkins-data:/var/jenkins_home `
  --volume jenkins-docker-certs:/certs/client:ro `
  --publish 8080:8080 --publish 50000:50000 myjenkins-blueocean:2.332.3-1