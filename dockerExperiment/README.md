This is untested work in progress.

## Build container

    sudo docker build -t singularity .

Then you would have to patch input and output to host.

## Run interactively

    sudo docker run -i -t singularity /bin/bash
    
## Mounting host

https://docs.docker.com/engine/tutorials/dockervolumes/#mount-a-host-directory-as-a-data-volume

Idea would be to patch container '/output' to some directory on host and the either run container interactively or with something like

    sudo docker run singularity toX264 /host/filesystem/someinput.mov

     _____ 
    < lol >
     ----- 
        \
         \
          \     
                        ##        .            
                  ## ## ##       ==            
               ## ## ## ##      ===            
           /""""""""""""""""___/ ===        
      ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~   
           \______ o          __/            
            \    \        __/             
              \____\______/   
              
## cpus

> Note for Mac/Windows users: the CPUs available to docker are limited by the host machine running docker, which on Mac/Windows is the virtual machine running in the localhost OS. To make more cores available to a docker container, make sure the host VM has enough cores. Example: docker-machine create --driver virtualbox --virtualbox-cpu-count 4 fourcpu. Then, containers will have access to 4 CPUs, which is verifiable with docker run <image name> nproc, which should print 4.

http://stackoverflow.com/questions/20123823/how-does-docker-use-cpu-cores-from-its-host-operating-system
