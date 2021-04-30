# create a docker container from a dockerhub image
    
    docker container run -it -p 80:80 nginx

#### -> here container is the management command for docker(you can find all in typing docker in terminal)

#### -> run is a subcommand(again find all by typing docker in terminal)

#### -> -it is another subcommand running the container in a interactive mode ..it will show log straight in the terminal after container runs and stables. And -d is for running the container is detached mode. so -d will run the container in the background and will not show logs straight ahead

#### -> -p is a tag to map the port, the port on the left side of the : is your computers port and the port on the right side is the port the container and these two ports maintains a tcp connection. So any request coming from your computer 80 port will be forwarded to containers 80 port

#### -> the last nginx is the image in dockerhub that it pulls from and builds a container...remember each container is built from a image that means you can run several container from a image. So, there can be multiple instances (container) of a image.

# List docker containers

## List running and stopped containers(two ways and ps is the old way)

    $: docker container ls -a
    
    $: docker ps -a

## List only running containers(two ways and ps is the old way)

    $: docker container ls
    
    $: docker ps

# List docker images
    
    $: docker images   
    
    REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
    nginx        latest    62d49f9bab67   2 weeks ago   133MB

# Delete docker image

    $ docker image rm 62d
   
#### -> Important Note: Sometimes need to add the -f flag if the image is being used by a container... 

# Pull a image from docker hub at any time

    -> docker pull nginx
    
    

    
