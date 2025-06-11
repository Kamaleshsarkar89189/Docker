# What is Docker ?

    Docker is an open-source platform used to develop, ship, and run applications inside ligtweight, portable containers. A container packages an application and all its dependencies(libraries, configuration files, environment variables, etc.) so it can run consistently across different computing environments.

# Why Docker Is Used in Software Development:

   1. Environment Consistency
   2. Isolation
   3. Portability
   4. Efficiency
   5. Scalability & Microservices
   6. Simplified Deployment & CI/CD

# Docker Commands:

    1. docker pull image_name
    2. docker images (to see all images in docker)
    3. docker run image_name
    4. docker run -it image_name (to run docker container interactive mode)
    5. docker ps -a (to see how many container exists)
    6. docker ps (to see running containers)
    7. docker start cont_name or cont_id(to start any container)
    8. docker stop cont_name or cont_id
    9. docker rm (to remove container)
    10. docker rmi image_name(to remove image)


    11. docker pull image_name:version(to install specific version) 
    12. docker run -d image_name(to run a container in background, {-d represents detach  mode})
    13. docker run --name container_name -d image_name(to name the container )

# Docker Image Layers

    Container
        |
    Layer 2
        |
    Layer 1
        |
    Base layer --> Linux (DBN, alpine)

# Port Binding

    Every container's have a port. All container's ports are separate as compare to host machine

    . docker run -p8080:3001 image_name 
    
# Troubleshoot Commands

    . docker logs cont_id
    . docker exec -it cont_id/bin/bash (allows us to run auditional commands on an alraady running container)
    . docker exec -it cont_id/bin/sh (Alternative method)