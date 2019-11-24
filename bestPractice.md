# Docker-Compose Notes  

## Basic 

``` yaml
version: '3.7'
services:
 redis: 
   # use alpine whenever possible
    image: redis:4.0.9-alpine
   # add this 
    init: true
    container_name: redis
``` 

``` yaml
version: '3.7'
services:
 redis: 
   #use env to store setting values
    image: redis:${IMAGE_LABEL}
   # add this 
    init: true
    container_name: redis
```

``` bash
# Use the build flag to rebuild your containers
docker-compose up -d --build
```


## Network

``` yaml
# create new network with default pattern
version: '3.7'

services:
  web:
    build: .
    # HOST_PORT:CONTAINER_PORT
    ports:
      - '8000:8000'
  db:
    image: postgres
    ports:
      # HOST_PORT:CONTAINER_PORT
      - '8001:5432'
# automatical create network name called 
# ${COMPOSE_PROJECT_NAME}_default 
```

``` yaml
# create new network with custom setting
version: '3.7'

services:
  proxy:
    build: ./proxy
    networks:
      - frontend
  app:
    build: ./app
    networks:
      - frontend
      - backend
  db:
    image: postgres
    networks:
      - backend

networks:
  frontend:
    # Use a custom driver
    driver: custom-driver-1
  backend:
    # Use a custom driver which takes special options
    driver: custom-driver-2
    driver_opts:
      foo: '1'
      bar: '2'

```

``` yaml
# use predefined network
version: '3.7'

services:
  web:
    build: .
    ports:
      - '8000:8000'
  db:
    image: postgres

networks:
  
  default:
    # Use a custom driver
    driver: custom-driver-1

```
``` yaml
# use pre-existing network
version: "3.7"

services:
  app:
    image: whatever
  networks:
    - my-network

networks:
  my-network:
    #(compose v3.4 and higher you can use it with other network configuration keys)
    external:
      name: my-network-name
```



## References
1. [Docker-compose Tricks and Best Practices](https://medium.com/factualopinions/docker-compose-tricks-and-best-practices-5e7e43eba8eb)
2. [Yaml Templates](https://medium.com/@kinghuang/docker-compose-anchors-aliases-extensions-a1e4105d70bd)
3. [alpine](http://gliderlabs.viewdocs.io/docker-alpine/)
4. [alpine-1](https://thenewstack.io/alpine-linux-heart-docker/)
5. [docker-compose network setting](https://titangene.github.io/article/networking-in-docker-compose.html)
6. [docker-network in compose](https://docs.docker.com/compose/networking/)
7. [docker-compose in production](https://docs.docker.com/compose/production/)

