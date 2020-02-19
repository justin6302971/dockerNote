# Docker-Compose cheatsheat
> navigate to the target directory where docker-compose.yml files are located


## sample yml file
``` yaml

version: '3.7'

services:
  #service name
  web:
    build: .
    ports:
      - '8000:8000'
  db:
    image: mysql:8.0.18
    ports:
      # HOST_PORT:CONTAINER_PORT
      - '3309:3306'
    volumes:
      - dbvolume:/var/lib/mysql
volumes:
  #volume name
  dbvolume: 
```
## basic
``` bash

#test if yml files format is working 
docker-compose config

docker-compose stop SERVICENAME

docker-compose restart SERVICENAME
```

## run containers 
``` bash
# read default docker-compose.yml and docker-compose.override.yml 
docker-compose up -d 

# with certain yml files (order is important)
docker-compose -f YOUR_FILE_NAME up -d

```

## stop and delete containers
``` bash
# stop and remove containers
docker-compose down

# with certain yml files (order is important)
docker-compose -f YOUR_FILE_NAME down

# also remove images used by containers
docker-compose down -rmi all

# also remove volumes that containers used(notice it will remove related mounted data)
docker-compose down -v
```



