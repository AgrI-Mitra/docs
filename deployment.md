# Deployment Documentation

## Setup

1. [Install Docker](https://docs.docker.com/engine/install/ubuntu/)

## Steps to Deploy

1. Clone the [devops](https://github.com/agri-mitra/devops) repository
2. Navigate to directory named *combined* path - home/ubuntu/devops/combined
3. Create a .env file and add the environment variables
4. Start the services using  the command ```docker compose up -d```

## Steps to redeploy a service

You can redeploy a particular service using below command

```docker compose up -d {service-name} --build```

E.g., 

To deploy bff service, run

```docker compose up -d bff --build```

## Other Information

1. We use github packages to store the docker images of services. Whenever new code is pushed to the repository a new image is automatically built and stored in Github Packages.
2. For public services like *nginx*, we use the docker images hosted at Docker Hub


