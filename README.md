# dc-stack
docker compose stacks

# How to run

Clone this repo 

```bash
git clone <this repo>
```

build app image

```bash
cd app
docker build -t html-server:1.0 . 
```

build load balancer
```bash
cd load-balancer
docker build -t load-balancer:1.0 .  
```

up this stack using docker-compose
```bash
cd ..
docker-compose up
```

testing - in a separate terminal run
```bash
curl localhost:8080
```

and check docker compose logs
