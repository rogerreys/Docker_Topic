# RUN
	docker container run -t ubuntu top
# Inspect the container
	docker container exec
# Connected to node1
	ssh IP
	ssh 192.168.0.11
# Get the ID of the running container
	docker container ls 
# Use that container ID to run bash inside that container 
Use the -it flag to run using interactive mode while allocating a psuedo-terminal
	docker container exec -it b3ad2a23fab3 bash
# Namespaces 
    PID: Process ID
    MNT: Mount and unmount directories without affecting other namespaces.
    NET: Containers have their own network stack.
    IPC: Isolated interprocess communication mechanisms such as message queues.
    User: Isolated view of users on the system.
    UTC: Set hostname and domain name per container.

