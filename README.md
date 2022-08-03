# Docker_Topic

1. Open a terminal on your local computer and run this command:

    & docker container run -t ubuntu top

2. Inspect the container:

    & docker container exec

This command allows you to enter a running container's namespaces with a new process.

3. Open a new terminal. To open a new terminal connected to node1

    ssh 192.168.0.18

4. In the new terminal, get the ID of the running container that you just created:

    docker container ls 

5. Use that container ID to run bash inside that container by using the docker container exec command. Because you are using bash and want to interact with this container from your terminal, use the -it flag to run using interactive mode while allocating a psuedo-terminal:

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