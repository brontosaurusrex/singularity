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
