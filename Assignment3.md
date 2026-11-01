 Kubernetes    is a container orchestration which is a tool that manage multiple containers across a group of machine or cluster . 

For Deploy the application we talk to k8s and it will handling tool like Docker and anyone similar tool.

     It runs container in dittached mode only 

creating a containers using docker on a single machine that doesn't have the capability to create multiple containers .

automation on top of docker is called container orchestration . 

  Container orchestration is the process of automating the scheduling  , deployment , n/working ,                  scaling  , management of containers across a cluster of server in a desired and consistent state.

cluster means group of machines in k8s . 

FOR DEPLOY THE APPLICATION WE NEED SOME TOOLS  LIKE ,

->  Kubctl : k8s controller

->   kind    : k8s inside the machine 

                    using kind create two containers and container will be acting as  a docker machine 

    -YAML file 

 ---# CMD  : anything on the right hand of hash is consider as Command . On left  will read .

in   YAML FILE every line will have something that is a key followed by a value .

  2 . k8s objects 

Pods :- basic and simplest object in cluster . 1 pod define one container 

pod is to deploy the application 

1 main container and other will be side cars .

to create , 

    $kubclt apply -f pod1.yml 

without going inside the container , if wants to run same commands 

      $ kubctl  exec testpod --env 

minimum resource pods to use : request

maximum resource pods to use : limit

remove kubctl  : $kubctl <command ><type><name of object>

                                      eg : $kubctl get pods        

LABELS AND SELECTORS 

Name we attach to an object 

we can select a label and it will refer to corresponding obj .

we will put label in metadata .

labels are used to identify object .every object have its own label name 

if we want to create pods on specific machine , we need to apply label on the machine and with node selector we able to create pod 

e g : kind : pods 

            api version : v1

              metadate : 

                      name : labelpod 

               labels;

                          my name : NANDA

                          my org : WEZVATECH

$kubctl get pods --show - labels 

node Selector :                                          # specifies which node to run the pod 

  my node = demoname

 $ kubctl  get label node 

any application or micro service we take divide them into two categories 

1) statefull application : if the application stores some information or meta data in the sameplace where the application is running . like , it can store in the same machine where it is running or in terms of containers it can store information about whatever the application needs inside the same container or port eg :MYSQL

2)stateless application : Run the application the container or the machine or make how many copies want, but it would not storing the data inside it. it will store the data whatever the applications wants outside the container/machine on a separate db.eg: AMAZON,GOOGLE 

REPLICATION OBJECT

Deployment obj : it is needed for running our stateless application . 

Rollback : take the previous one (go back). $ kubctl rollback undo modifying applying with create new pods then the existing pod will deleted , enable the previous one 

Rollout : just deploying 

deploy (delete new ports that into old ports)

replace the existing with the new one 

deployment obj creates replicas on any machines capacity is available . use in stateless applications .

Deamon set : used in third party application , need one copy in every machine . worker nodes use                                  deamon  

Statefull set : deploying statefull application.

Replica set: create, scale and replicate the pods 

CONFIGURATIONS STORAGE OBJECTS 

Configmap: stores nonsensitive configuration data as key-value pairs that can be injected into containers 

Secret : Enrcypts and stores sensitive data like password or SSH keys 

Persistent volume (PV): its an object which helps to make sure content inside the volume its always available . eg: $ kubctl apply - f  pv.yml

:- volumes : its a shareable folder , if we want to put something inside the container . storage within the pod, as  long as pod available volume is also available .

Different type of volume :- 

                                             emptydir

                                             persistent volume 

Persistent volume claim : a request for storage by a user that binds automatically to a matching pv.

NETWORKING OBJECT 

Service : access the service , the service will redirect to the pod.

four types:- 

                 1) cluster ip : we access service redirect ports . while accessing it  it will be container 

                 2) Nod port : range 30000 to 32767. access in outside the cluster 

                 3) Loadbalancer 

    
