# Docker vs Virtual Machine(VM)

    Application Layer
            |
    Host OS Kernel
            |
        Hardware

# 🔧 1. Architecture
Virtual Machines:

VMs run on a hypervisor (like VMware, VirtualBox, or Hyper-V).

Each VM includes a full guest OS, libraries, and the application.

Requires more system resources (CPU, RAM, disk).

Docker (Containers):

Docker runs on the host OS kernel using a container engine.

Containers share the host OS kernel but have isolated user spaces.

Much lighter and faster than VMs.

        Use Docker when you need lightweight, fast, and scalable application environments.

        Use VMs when you need full OS-level isolation, run multiple OS types, or support legacy applications.

# Docker Network

        docker network ls
        docker network create NEWTWORK_NAME
        
# Mongo setup

        settign up mongo & mongo-express

        mongo setup

        docker run -d \
        > -p27017:27017 \
        > --name mongo \
        > --network mongo-network \
        > -e MONGO_INITDB_ROOT_USERNAME=admin \
        > -e MONGO_INITDB_ROOT_PASSWORD=qwerty \
        > mongo

        mongo express setup

        docker run -d \
        > -p8081:8081 \
        > --name mongo-express \
        > --network mongo-network \
        > -e ME_CONFIG_MONGODB_URL="mongodb://username:password@mongo:27017"


# Docker Compose
        
        Docker Compose is a tool for defining and running multi-container applications.

version: "3.8"

services:
     mongo:
        image: mongo
        port:
         -27017:27017
        environment:
          MONGO_USERNAME: username
          MONGO_PASSWORD: pass

# 📦 Summary of Common Keywords

| Keyword       | Description                              |
| ------------- | ---------------------------------------- |
| `version`     | Compose file format version              |
| `services`    | Group of containers (services)           |
| `build`       | Build image using Dockerfile             |
| `image`       | Use a prebuilt image instead of building |
| `ports`       | Map host\:container ports                |
| `environment` | Pass env variables to container          |
| `volumes`     | Mount host folders into container        |
| `restart`     | Container auto-restart policy            |
| `depends_on`  | Start order for containers               |
| `command`     | Override the container’s default command |
| `networks`    | Custom networking between services       |


# Commands

docker init

docker compose up

docker compose watch

docker compose -f fileName.yaml up -d (it represents that we want to run or start, all containers are defined in that file)

docker compose -f fileName.yaml down (to delete all containers )

docker network ls (to see all network )

# Publishing Images

        docker built -t kamalesh89189/repo

        docker login // to check logged in or not

        docker tag repo_name kamaleshsarkar89189/repo_name

        docker push kamaleshsarkar89189/repo_name

# Docker Volumes

        A Docker Volume is a persistent storage mechanism used to store data outside of a container's lifecycle. This means even if your container stops, crashes, or gets deleted, the data stored in a volume remains safe.

        ✅ Why use volumes?
        Data persistence (e.g. for databases like MongoDB, Postgres, etc.)

        Share data between containers

        Backups and portability

        Isolate app code from container file system

# Commands
        docker volume ls // to see all volumes
        docker volume create vol_name 
        docker volume rm vol_name // to delete any volume

        docker run -v my-volume:/app/data my-image
# docker-compose.yaml
services:
  mongo:
    image: mongo
    volumes:
      - mongo-data:/data/db

volumes:
  mongo-data:

Here, mongo-data is the volume name and /data/db is the path inside the container where MongoDB stores its data.
 
Named Volumes 
        docker run -v vol_name:cont_dir

Anonymous Volumes
        docker run -v mount_path

Bind Mount
        docker run -v host_dir:cont_dir

# 🧹 docker volume prune — What It Does

        docker volume prune

        deletes all unused (dangling) Docker volumes — i.e., volumes not currently used by any container.
