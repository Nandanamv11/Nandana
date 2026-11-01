we need to build Docker Image for our application because it packages  the application code, runtime , system tools , and libraries into a single  , immutable artifact .

 Before Developing a Docker file to build a image we need 

     BASE ENVIRONMENT AND RUNTIME 

      :-  programming language and version  : identify the exact version our code runs on ( e g : ubuntu ,                                                                                    JDK17 ) 

     APPLICATION SOURCE AND ARTIFACT DEPENDENCY 

      :- dependency files : locate the exact package manifest file required  by our language package                                                       manager( e g : package .json , requirments.txt)

      :- Build Tools : determine if the code requires a compiler or build tool to generate executable binaries(                                 eg : Mevan , npm) can run.

       :- ignored artifacts : identify which local development folders or files must be kept out of the                                                           container ( eg : node_modules , .git , local.env files  )

     EXECUTION AND START UP INSRTUCTIONS

 

       :- the main execution command : eg : node server . js 

       :- overridable  vs. fixed entrypoints : decide whether the application container needs to behave like a                                                                         strict command-line executable  ( ENTRYPOINT) or  allow user to                                                                       easily pass diff runtime arguments (CMD).

 

     NETWORK AND STORAGE COFIGURATION 

      :- port allocation : find out which specific TCP/UDP  port our application listens to internally so we can 

                                    document it using the EXPOSE instruction ( port 8080 , 3000 )

       :- pv(persistent  volume ) : outside the cluster , which helps to make sure content inside the volume is                                                      available  .( like user uploads or localized  db ) 

     SECURITY AND RUNTIME VARIABLES  

         :- environment variable : collect the list of configuration  keys (ENV) that must be set during runtime                                                        or compilation parameters (ARG) required during the build phase . 

every time when a developer modifies into take the code , we are going to build by running Mevan and build the image by execute docker build command and then do a smoke test and if the execution successful push image to respective registry .  

open a docker file there will be two column separated  by same space . 1st column will be in capital ,    called as INSTRUCTIONS . 2nd column is the value what we wants to pass to the column . or it can be a command that we wanted to run inside the intermediate container .

         INSTRUCTION                    Commands

FROM                                 <Base image>     :  image for creating intermediate container 

RUN  (copy)                       <Command>       :  to run OS CMD inside  the intermediate container 

CMD                                ["executable","arg1","arg2"]  : user and will override the default CMD

ENTRYPOINT                 ["executable","arg1","arg2"]   : always runs default CMD , user CMD is taken as                                                                                                  argument .

COPY                              <SRC><DEST>      : copies files from docker host to image 

 ADD                               <SRC><DEST>       : extract a archive or download a file from a URL directly 

USER                               <USERNAME>        : sets a default user 

WORKDIR                        <PATH>                   : sets a default working directly 

ENV                                 <VARNAME>=<VALUE> : variable visible in image 

AGR                                  <VARNAME>=<VALUE> :  "            "         in temp container , not an image 

EXPOSE                            <PORT>                    :  when a user creates a container from an image                                                                                               whatever all ports number that it should be visible for                                                                                       the user not the MAPPING 

 $docker build -t <image name>:<Tag Name>  : .(DOT) dot mean the context of current folder .pick the file and everything that we need in docker file .

  suppose the docker file in a different location or diff name of file that we use -f and give that file  ( e g : -f <Docker file-location>).

 3 .  -> structure of DOCKER image

            building a docker image , create a file named DockerFile

       -> a docker file is a text file that contains s set of instructions for building a Docker image .

              its like a layered cake . every layer is read-only ,staked one over other .

          A docker image not one  single file. its made of multiple layers 

 in k8s , actual image structure inside the registry

             in  kubernetes itself does not build the image . it olny pulls and runs the image we already built.

         

                   push   my-app:v1 , it has 3 parts :-

              1)     manifest (manifest .json) 

                       index file 

                       k8s Kubelet reads first to know what to download

             2)   layers (tar files)

                 each layer is a .tar file with a SHA hash

                    e g : layer 1   Alphine os

                                      2 Jdk/python libs

                                      3  app . jar

there are read only and shared . if 10 pods on same Node use same layer 1 , Node stores it only once .

             3) config

            metadata  : what Cmd to run , Env vars , port , working directory 

                                e g : Cmd : ["java","-jar","app.jar"]  

DOCKER HUB  

      my-app : v1

       manifest.json (points to layes )

       config.json (run cmd , env )

      layer 1. os

      layer 2.dependencies

      layer 3. our code 

