# Docker_Topic

## 1. Run a container
1. Open a terminal on your local computer and run this command:

    & docker container run -t ubuntu top

2. Inspect the container:

    & docker container exec

This command allows you to enter a running container's namespaces with a new process.

3. Open a new terminal. To open a new terminal connected to node1

    ssh 192.168.0.18

4. In the new terminal, get the ID of the running container that you just created:

    docker container ls 

5. Use that container ID to run bash inside that container by using the docker container exec command. 
    Because you are using bash and want to interact with this container from your terminal, use the -it flag to run using interactive mode while allocating a psuedo-terminal:

    $ docker container exec -it b3ad2a23fab3 bash 
    root@b3ad2a23fab3:/#

Using docker container exec with bash is a common way to inspect a Docker container.
After you run the command docker container exec, the group of processes running in isolation (in other words, the container) includes top and bash.

6. From the same terminal, inspect the running processes:

    $ ps -ef


PID is just one of the Linux namespaces that provides containers with isolation to system resources. Other Linux namespaces include:

MNT: Mount and unmount directories without affecting other namespaces.
NET: Containers have their own network stack.
IPC: Isolated interprocess communication mechanisms such as message queues.
User: Isolated view of users on the system.
UTC: Set hostname and domain name per container.



## 2. Run multiple containers
1. Explore the Docker Store.
2. Run an NGINX server by using the official NGINX image from the Docker Store:

    $ docker container run --detach --publish 8080:80 --name nginx nginx

The --detach flag will run this container in the background. 
The publish flag publishes port 80 in the container
The --publish flag is a feature that can expose networking through the container onto the host.
The --name flag, is the names the container. 

3. Access the NGINX server on http://localhost:8080.
4. Run a MongoDB server. You will use the official MongoDB image from the Docker Store.
    
    $ docker container run --detach --publish 8081:27017 --name mongo mongo:3.4

5. Access http://localhost:8081 to see some output from Mongo.
6. Check your running containers:
    
    $ docker container ls

You can see the nginx and mongo names that you gave to the containers and the random name
if container is running the "docker-entrypoint" command. so image requires some prior 
configuration before kicking off the DB process.


Containers are self-contained and isolated, which means you can avoid potential conflicts
For example, you  can deploy an app that uses Java 7 and another app that uses Java 8 on 
the same host.

Running multiple containers on the same host gives us the ability to use the resources 
(CPU, memory, and so on) available on single host. This can result in huge cost savings for an enterprise.



## 3. Remove the containers

1. Get a list of the running containers:

    $ docker container ls

2. Stop the containers by running this command for each container in the list:

    $ docker container stop [container id]
    // You can also use the names of the containers that you specified before:
    $ docker container stop d67 ead af5

3. Remove the stopped containers. The following command removes any stopped containers, 
    unused volumes and networks, and dangling images:

    $ docker system prune
