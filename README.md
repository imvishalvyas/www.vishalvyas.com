
In the previous article we have shown that how to install docker service in linux server, Now in this article i will explain some useful docker command which we are using daily basis.




### Some useful Docker commands.



Docker search 
Docker pull 
Docker images
Docker rmi
Docker run
Docer ps
Docket exec
docker rm 
Docker kill
Docket start
Docket stop 




### 1. Use docker command to search for nginx image, it will show the list of all availible nginx image from dockerhub.
```
docker search nginx 
```
















### 2. Use docker command to download the nginx image, , it will search images first in your local machine, if image is not availible in local machine then it will download image from docker machine.


```
docker pull nginx
```





















### 3. to check image is download or not. below command will show you all downloaded images of your local machine.

```
docker images
```
















### 4. Use docker command to remove an image


```
docker rmi nginx 
```




Now we will create a container from an image,



`Image`: images are like a code we can download and run it.

`Container` : It's execute code and providing service, Running instance of an image is known as a container.





### 5. Use docker command to run the nginx image, we will also map it's port 8080 of instance to port 80 of container.


```
docker run -d -p 8080:80 nginx 
```

where `-d` will run the Nginx service in background and `-p` for port.













Now we will check the nginx service run or not from browser, using Yourip:8080 , great it is working fine.






















### 6. Use docker command to list all running & stopped containers


```
docker ps 
```
```
docker ps -a
```










### 7. Use docker command to connect to a running container


###
docker exec -ti nginx /bin/bash
###


Where `-t` means Terminal TTY and `-i` means Interactive 





### 8. Use docker command to remove running of stopped container. you will have to first stop the container and then you can able to delete docker container.


```
docker rm {Container ID}
```




### 9. to Kill one or more running containers.


```
docker kill {Container ID}
```










### 10. To Start one or more stopped containers.


```
docker start {Container ID}
```


### 11. To Stop one or more running containers


```
docker stop {Container ID}
```






So we have learn all docker useful commands here . If you want to practice all commands and you dont have any machine then below website is very cool for the practice docker online, it will provide complete docker machine for 4 hours for practice and you can create maximum 5 nodes there.


```
https://labs.play-with-docker.com/
```






























Thanks, next article i will explain more docker commands and some services which we can run from docker.





Article written by VishalVyas
