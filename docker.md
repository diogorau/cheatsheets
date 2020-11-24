#  Docker

## Search
### Find an image on dockerhub
    docker search diogorau


## Pull
### Retrieve an image onto local host
    docker pull ubuntu
    docker pull ubuntu:latest  # Same as above
    
    
## List images
    docker images  # Also "docker images -ls"
    docker images -a  # Shows all intermediate images
    docker image history myimage  # Show the layers of an image
    

## Create a container
### Instantiates an image, but does not start it
#### use a shell through `-i` (or `--interactive`) and `-t` (or `-tty`)
    docker create -it ubuntu  # An instance with a command line
    docker create -it --name foo ubuntu  # Same, but in a container named "foo"
    docker create -it --name foo ubuntu sh  # Run sh instead of default shell
    docker create -it -v /Users/diogo/Desktop:/desktop ubuntu  # Mount my desktop inside the container
    docker create -it -p 8080:80 ubuntu  # Map port 80 in the container to 8080 in the host
    docker create -it -e VAR1 --env VAR2 --env-file ./env ubuntu  # Set environment variables
    
    
## Start
### Start interactively
    docker start -i foo
    docker start -ia foo  # Also attach STDERR, and signals


## Run
### Run does both `create` and `start`
    docker run --it myimage  # Start myimage in a new container, interactively
    docker run --name foo -it myimage  # Same, but name the container "foo"
    docker run --name foo -it --rm myimage  # Same, but auto remove container when it exits
    docker run --rm --name foo ubuntu /bin/echo "Hello world"  # Run "echo"; no need for interactivity
    docker run --rm ubuntu ls -al  # Run commands in the container
    docker run -w /root -it ubuntu  # Start in the /root working directory
    docker run -it -p 8080:80 ubuntu  # Map port 80 in the container to 80 in the host
    docker run -d -p 8080:80 myserver  # Run detached process, i.e., in the backgruond

## Mounting volumes
### Create a named volume for persistance
    docker volume create my-db  # Now your can docker run -v my-db:/local_volume
    docker run -v /Users/diogo/Desktop:/desktop ubuntu  # Mount my desktop inside the container
    
### Use a bind mount
    docker volume inspect  # See where tho volume lives


## Execute within a container
    docker exec -it foo /bin/bash  # Launch a shell within a running container

## List containers
    docker ps  # All running containers
    docker ps -a  # All containers, including stopped
    docker ps -aq  # All containers, but just the IDs
    
## Stop containers
    docker stop foo
    docker stop -t 10 foo  # Wait 10 seconds before killing the container

## Remove containers
    docker rm e6f7  # Using just the start of the container ID
    docker rm foo  # Using the container's name
    docker rm $(docker ps -aq)  # Remove all stopped containers
    docker rm -f foo  # Remove foo, even if it is running, stopping it first

## Remove images
    docker rmi ubuntu
    docker rmi diogorau/foo-image:latest  # Remove by specific tag 


## Build an image
    docker build .  # Build from the Dockerfile in the current directory
    docker build -f Dockerfile.bak .  # Build from a different Dockerfile
    docker build -t diogorau/foo .  # Build and tag this
    echo "FROM ubuntu" | docker build -t simple -  # Build from command line, without a Dockerfile
    
## Tag
    docker tag localcopy diogorau/foo:latest
    
## Push
    docker push diogorau/foo  # Send the new image to Docker Hub
    
## Dockerfile
    FROM ubuntu:latest  # Use the most recent version of Ubuntu
    
    ARG HOME=/home  # Set an argument that can be used later as $HOME
    
    # Run commands from the command line. Chain with &&
    # so that the build fails if the first step fails.
    RUN apt-get update && \
        rm -rf /var/lib/apt/lists/*
        
    # Creating a directory called start, and work from there
    WORKDIR /start
    
    # Copy all the files in this directory to the working directory
    COPY . .
    COPY requirements.txt /root/
    
    # Set an environment variable to the value 1
    ENV IN_CONTAINER 1
    RUN unset NOT_IN_CONTAINER # Unset another variable
    
    # Change current directory to /start/app
    WORKDIR app
    
    # Execute commands; Unlike RUN, these can be overridden when the
    # container is started, e.g., through "docker run -it foo /bin/bash"
    CMD echo "Hello world!"  # Run the main app; this can be overrriden
    CMD ["/bin/echo", "Hello world!"]  # A safer way to do it
    
    # Or, instead of CMD, use ENTRYPOINT to run a command line option
    # Now you can execute 'docker run -it foo --help' as if you were
    # running 'docker run -it foo /bin/bash myapp.py --help'
    ENTRYPOINT ["myapp.py"]  
    ENTRYPOINT ["exec", "myapp.py"]  # Better, because myapp will get signals (e.g., SIGTERM when docker stop occurs)
    CMD ["--verbose"]  # Sets myapp to run --verbose, unless overridden
