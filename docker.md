### Create docker file : 
To deploy static website we will have to create one docker file to run website. in docker file we will add some text to perform tasks. copy the content below and paste in your docker file.

* Create directory called docker [you can create any]
```
mkdir /docker
```

* Create docker file in to docker directory and add below context.
```
vim dockerfile
```
```
FROM nginx:alpine

COPY . /usr/share/nginx/html
```

save file.



### 1. it will download nginx latest from docker hub.

### 2. copy all context from working directory to /usr/share/nginx/html.

```
touch index.html
```
```
<h1>Hellow this is my website</h1>
```

and save the file.



Now we will build the docker image. from the build command it will execute each instruction which we have added in docker file.

```
docker build -t mywebserver:v1 .
```
```
Sending build context to Docker daemon 3.072 kB

Step 1/2 : FROM nginx:alpine

alpine: Pulling from library/nginx

ff3a5c916c92: Pull complete

d81b148fab7c: Pull complete

f9fe12447daf: Pull complete

ad017fd52da2: Pull complete

Digest: sha256:4a85273d1e403fbf676960c0ad41b673c7b034204a48cb32779fbb2c18e3839d

Status: Downloaded newer image for nginx:alpine

 ---> bc7fdec94612

Step 2/2 : COPY . /usr/share/nginx/html

 ---> 86c5b4596840

Removing intermediate container 8a769ed68528

Successfully built 86c5b4596840
```

Now you can see that build is success and downloaded nginx. we will check image using below command.
```
docker images
```
```
REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE

mywebserver         v1                  86c5b4596840        About a minute ago   18 MB
```

Now we will run the image and launch the container from the image. i will bind it port to 9090 as i have already use 80.


```
docker run -d -p 9090:80 mywebserver:v1

31e18bf6c0337b69ded3328ad7affa45bf68f31253152e12ce099a1a13151975
```


i have define name of container [mywebserver and tag v1]



* Now you can see that our container is running. 


```
docker ps
```
```
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                  NAMES

31e18bf6c033        mywebserver:v1      "nginx -g 'daemon ..."   37 seconds ago      Up 35 seconds       0.0.0.0:9090->80/tcp   amazing_clarke
```




Now you can check from web browser using host IP.
