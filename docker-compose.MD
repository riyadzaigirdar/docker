# create a container using dockerfile and docker-compose.yml

#  create the docker file

### Dockerfile (FROM, MAINTAINER, WORKDIR, MKDIR, RUN, EXPOSE, CMD(array))
  
    FROM nginx:latest

#### it will install nginx in debian operating system

    MKDIR app

#### it will create a folder app in the container operating system

    COPY ./ /app
   
#### it will copy all the files in your dockerfile directory to the container os /app folder

    EXPOSE 80

#### expose a port from the container which you can map in docker-compose file

    RUN python manage.py runserver
    
    CMD ["python", "manage.py", "runserver"]
    
### Docker compose yml file

#### In docker compose yml file can have three 1st column directives
    
    version: 
        ...
    services:
        ...
    jobs: 
        ...

#### choose a version
    
    version: "3"
    
#### then in services write your services one by one in 2nd column

    sercices:
        app:
          ...
        mysql:
          ...
        mongo:
          ...

#### inside each service you can build , map runtime volumes, expose ports(must), input commands(multiple), link services or depens on directives, set env variables

    services:
        app: <-- service name
          conitainer_name: python-app-container <-- name the container so you can detect in docker ps -a
          
          restart: always <-- restart if anything changes in the service
          
          build: . <-- point to the specific docker file directory
          
          build: <-- you can also write it like that for flexible
          
            context: .
            dockerfile: Dockerfile.Development
            
          ports: 
          
            - "80:80" <-- right side port is the the container running  the application and left port is the port is the port our pc...both ports are mapped to each other
          
          volumes:
          
            - ./: ./app <-- map the folder in the container /app directory to detect run time changes
            
          environment:
          
            - DB_HOST=db
            - DB_NAME=app
            - DB_USER=postgres
            - DB_PASS=supersecretpassword
          
          depends_on: < -- it will wait for db service to start and link with db service and host and folders inside container not accessible by other container
          
            - db
            
          link: < -- it will only link with db service and host and folders inside this container accessible by other container and services
          
            - db
          
          commands: >
             sh -c "python manage.py wait_for_db &&
                    python manage.py migrate &&
                    python manage.py runserver 0.0.0.0:8000"
                
    
    
