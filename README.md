# Assignment task 

# Setup and Deployment 

## Clone the repository

```bash 
git clone https://github.com/parths-rk/crud-dd-task-mean-app

cd crud-dd-task-mean-app

docker compose build

docker compose up -d

docker ps # verify


```
# http://localhost # open in browser

# Workflow

1. code pushed to github
2. jenkins pipeline triggered
3. Docker images built
5. images pushed to docker hub
5. containers redeployed using docker compose 