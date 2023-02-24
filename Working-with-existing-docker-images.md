
# Working with existing docker images

## Verify what's currently on the dockerhost
```docker ps```  
![dockerps](https://user-images.githubusercontent.com/75420964/221122131-e82666f2-2d39-494d-8abe-39e6d18c0206.png)


```docker images```

![docker images](https://user-images.githubusercontent.com/75420964/221122397-c59e477e-e62d-48d6-94fa-f161f32d7ce5.png)

## Get an existing image from dockerhub 
- https://hub.docker.com/  
- search for "containerofcats"  
- click "acantril/containerofcats"  

![hub docker](https://user-images.githubusercontent.com/75420964/221126444-f3bbd689-2d61-4adf-ae44-cc1ffcb16ac9.png)

 
```docker pull acantril/containerofcats```   

*notice how it's pulling a few fs layers ..* 

![containerofcats](https://user-images.githubusercontent.com/75420964/221126236-314dee66-c83e-4a5f-926a-dcd2f9991f04.png)



## Working with the docker image & containers locally
  
```docker images -a```  
```docker inspect <imageID>```  

*Run a container from the downloaded docker image*    
```docker run -p 8081:80 acantril/containerofcats```  

![localhost 8081](https://user-images.githubusercontent.com/75420964/221128626-fe84b180-ce9a-4525-89bd-0e2f9986ac6f.png)

browse to it - see the cats? :)    

![cats seen](https://user-images.githubusercontent.com/75420964/221128819-1a0e9b1a-b85c-4813-bc53-5dce375b0a3f.png)


notice how the terminal is connected to the container  
if we ctrl+c to exit.. the container stops  
because the terminal is/was attached to the container  

```docker ps```  

we can run the container detached (-d), the terminal will drop back to the command prompt but the container is still running  

```docker run -p 8081:80 -d acantril/containerofcats```
 ![container-detach](https://user-images.githubusercontent.com/75420964/221136293-0616277d-fc3a-4142-b1dc-ab94badad876.png)
   
*now it's running and we can continue working and access the container.*

this command will show the port mappings, host:container (i'll cover this later in the course)   

```docker port <CONTAINERID>```  
![port mappings](https://user-images.githubusercontent.com/75420964/221136444-de56a3a1-5647-4adc-b5d9-22442ba08f91.png)

we can execute commands inside the container, dont worry if you don't see the qemu part it depends on your architecture  
 
```docker exec -it <CONTAINERID> ps -aux```  
![apache](https://user-images.githubusercontent.com/75420964/221136700-d23bc4a3-e5da-47e6-b4c3-e69b8190ace3.png)

You can even run a shell inside a running container    
```docker exec -it <CONTANERID> sh```  
![run-shell](https://user-images.githubusercontent.com/75420964/221136886-eec94be4-914f-4aff-8724-5440266cc1d8.png)
	
we can restart the container    
```docker restart <CONTAINDERID>```  

stop it  
```docker stop <CONTAINERID>```  
```docker ps```  
```docker ps -a```  

start it again  
```docker start <CONTAINERID>```  
```docker ps```  

we can show logs  
```docker logs <CONTAINERID>```  
add timestamps  
```docker logs <CONTAINERID> -t```  

## Let's cleanup all the things from this demo
Stop the running container    
```docker stop <CONTAINERID>```  
Remove the stopped container  
```docker rm <CONTAINERID>```  
List the images we have locally  
```docker images```  
Remove the image we pulled from dockerhub  
```docker rmi <IMAGEID>```  
	
![rmi delete](https://user-images.githubusercontent.com/75420964/221148398-d99d7bb3-7e4b-4c82-a287-247b2d8435be.png)









