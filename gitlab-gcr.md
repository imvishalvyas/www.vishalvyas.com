# How to configure gcr private images in GitLab ci

Recently I was configuring the GitLab pipeline using my own private docker image which is stored in the google cloud container registry. Below is my `.gitlab-ci.yml` file.

```
image: docker:19.03.12

variables:
  DOCKER_HOST: tcp://docker:2375
  DOCKER_DRIVER: overlay2
  DOCKER_TLS_CERTDIR: ""

services:
  - docker:19.03.12-dind

stages:
   - test
   
test:
  stage: test
  image: gcr.io/my-project/my-image:x1
  script:
    - mvn clean install -DskipTests
    - java -cp target/libs/*:target/test-classes:target/classes:config.properties org.testng.TestNG testng.xml
  allow_failure: true
  only:
    - test
  artifacts:
    name: reports
    when: always
    paths:
      - Reports
```

When I run this in CI pipeline, I got the below error [Failed to pull image with policy "always": Error response from daemon: unauthorized:].

## Error : 
```
Pulling docker gcr.io/my-project/my-image:x1...
WARNING: Failed to pull image with policy "always": Error response from daemon: unauthorized: You don't have the needed permissions to perform this operation, and you may have invalid credentials. To authenticate your request, follow the steps in: https://cloud.google.com/container-registry/docs/advanced-authentication (docker.go:147:0s)

ERROR: Preparation failed: failed to pull image "gcr.io/my-project/my-image:x1" with specified policies [always]: Error response from daemon: unauthorized: You don't have the needed permissions to perform this operation, and you may have invalid credentials. To authenticate your request, follow the steps in: https://cloud.google.com/container-registry/docs/advanced-authentication (docker.go:147:0s)
```

## Solution : 

1. I have create a service account key and download the json file.

2. Give the `Container Registry role` to the service account.

3. Run below command in your local pc to save the docker login credentials.
`Note` : 
- Username is _json_key (NOT the name of your service account)
- keyfile.json is the service account key you created.
```
docker login -u _json_key --password-stdin https://gcr.io < ./keyfile.json
```
It will save the credentials to this path `~/.docker/config.json`.

4. Copy the configuration present in `~/.docker/config.json` and create a variable name called `DOCKER_AUTH_CONFIG` in your GitLab project CI/CD variables. Now retry your pipeline and you can see that pipeline run with success.
