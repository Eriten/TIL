# Start Bash Session with a Specific User in a Docker Container

Normally when I wanted to start a bash session in a docker container, I would execute `docker exec -it <CONTAINER_ID> bash`. However, there are instances where you want to start a bash session with a different user, to do this, you can execute `docker exec -it --user <UID or USERNAME> <CONTAINER_ID>bash`


Reference: https://forums.docker.com/t/swiching-between-root-and-non-root-users-from-interactive-console/2269
