<div align="justify">

# Solución basada en servicios

## Índice

- [Crear red personalizada](#index01)
- [Crear volumen común](#index02)
- [Crear docker-compose](#index03)
- [Demostración de funcionamiento](#index04)

### Crear red personalizada <a name="index01"></a>

<img src="img/img01.png"/>

### Crear volumen común <a name="index02"></a>

<img src="img/img02.png"/>

### Crear docker-compose <a name="index03"></a>

```yaml
version: '3'
services:
  # ubuntu:
  #   build:
  #     context: .
  #     dockerfile: UbuntuDockerfile

  tomcat-app:
    image: tomcat:latest
    container_name: tomcat-container
    ports:
      - "8082:8080"
    networks:
      - tarea-8-network

  mariadb:
    image: mariadb:latest
    container_name: mariadb-container
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: exampledb
    volumes:
      - tarea-8-volume:/var/lib/mysql
    ports:
      - "3306:3306"
    networks:
      - tarea-8-network

  cloudbeaver:
    image: dbeaver/cloudbeaver:latest
    container_name: cloudbeaver-container
    ports:
      - "8978:8978"
    networks:
      - tarea-8-network

  mongodb:
    image: mongo:latest
    container_name: mongodb-container
    environment:
      MONGO_INITDB_ROOT_USERNAME: admin
      MONGO_INITDB_ROOT_PASSWORD: admin123
    volumes:
      - tarea-8-volume:/data/db
    ports:
      - "27017:27017"
    networks:
      - tarea-8-network

  mongo-express:
    image: mongo-express:latest
    container_name: mongo-express-container
    environment:
      ME_CONFIG_MONGODB_ADMINUSERNAME: admin
      ME_CONFIG_MONGODB_ADMINPASSWORD: admin123
      ME_CONFIG_MONGODB_SERVER: mongodb-container
    ports:
      - "8081:8081"
    networks:
      - tarea-8-network
  

volumes:
  tarea-8-volume:
networks:
  tarea-8-network:
```

### Demostración de funcionamiento <a name="index04"></a>

<img src="img/img03.png"/>
<img src="img/img04.png"/>

</div>