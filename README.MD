# create a docker container from a dockerhub image
    
    docker container run -it -p 80:80 nginx

#### here container is the management command for docker(you can find all in typing docker in terminal)

#### run is a subcommand(again find all by typing docker in terminal)

#### -it is another subcommand running the container in a interactive mode..it will show log straight in the terminal after container runs and stables.

#### -p is a tag to map the port, the port on the left side of the : is your computers port and the port on the right side is the port the container and these two ports maintains a tcp connection. So any request coming from your computer 80 port will be forwarded to containers 80 port
