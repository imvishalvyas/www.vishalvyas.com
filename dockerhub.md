# Create and publish your docker image on docker hub.


 Here in this note, I will tell you to how to upload your custom image to dokcer hub and make it public. You can upload your custom images to docker hub. So other people can also use that image in their applications. Docker Hub is the world's easiest way to create, manage, and deliver your teams' container applications. You can find many images on docker hub for your application. Also you can upload your custom image on it.
 

 ### Login to the docker hub.
First you need to login to the docker hub. Run the below command from your terminal to login.

```
docker login docker.io
```
It will ask you for enter usename and password.
```
Login with your Docker ID to push and pull images from Docker Hub. If you don't have a Docker ID, head over to https://hub.docker.com to create one.
Username: imvishalvyas
Password: ************
Login Succeeded
```

We now successfully authenticated docker hub login. So now you can upload your images to the docker hub. So now we have to create our custom image so that we can upload it to the dockerhub.

### Create custom docker image
I was searching image for kops, kubectl image for my pipeline somedays ago. But i couldn't found any matching image to my requirement. So I have created my custom image to use that tools included. I have make it to the public so other peoples also can use that image.

# Dockerfile

```
FROM alpine:3.10
MAINTAINER imvishalvyas
RUN apk --no-cache add ca-certificates \
  && apk --no-cache add --virtual build-dependencies curl \
  && curl -LO  https://github.com/kubernetes/kops/releases/download/1.15.0/kops-linux-amd64 \
  && mv kops-linux-amd64 /usr/local/bin/kops \
  && curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.17.0/bin/linux/amd64/kubectl \
  && mv kubectl /usr/local/bin/kubectl \
  && chmod +x /usr/local/bin/kops /usr/local/bin/kubectl \
  && apk del --purge build-dependencies

ENTRYPOINT ["/usr/local/bin/kops"]
CMD ["--help"]
```

### let's build it.

```
docker build -t kops:v1 .

```

### Tag the docker image. 
You should use your docker hub username in image tag. In my case it's `imvishalvyas`.

```
docker tag kops-kubectl:v1 imvishalvyas/kops-kubectl:v1
```

### Upload it to docker hub. 
In the previous step we already login to the docker hub account using command. Now we will push the image to the docker hub account.

```
docker push imvishalvyas/kops-kubectl:v1
```
As you can see now that image is published successfuly on the docker hub. Now you can use that image anytime you want and also you can share that image to your group to use that image.
