<div align="justify">

# Construcción de Dockerfile

## Índice

- [Crear red personalizada y volumen](#index01)
- [Crear Dockerfile](#index02)
- [Construir y ejecutar imagen](#index03)

### Crear red personalizada y volumen <a name="index01"></a>

<img src="img/img01.png"/>

### Crear Dockerfile <a name="index02"></a>

<img src="img/img02.png"/>

### Construir y ejecutar imagen <a name="index03"></a>

```Dockerfile
# Usar una imagen base de Ubuntu para las instalaciones adicionales
FROM ubuntu:20.04

# Instalar dependencias necesarias (como wget y curl)
RUN apt-get update -y && \
    apt-get install -y \
    wget \
    curl \
    unzip \
    mysql-client \
    && rm -rf /var/lib/apt/lists/*

# Configurar MariaDB usando la imagen oficial
FROM mariadb:latest

# Volúmenes para MariaDB    
VOLUME /var/lib/mysql

# Configuración de MariaDB: Establecer la contraseña root y crear la base de datos (esto es suficiente con las variables de entorno)
ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=exampledb

EXPOSE 3306

# Configurar Tomcat usando la imagen oficial
FROM tomcat:latest

COPY ./assets/sample.war /usr/local/tomcat/webapps

EXPOSE 8081

# Descargar y configurar CloudBeaver utilizando la imagen oficial de CloudBeaver desde Docker Hub
FROM dbeaver/cloudbeaver:latest

# Exponer puertos
EXPOSE 8978

# Iniciar los servicios de MariaDB, Tomcat y CloudBeaver
CMD service mysql start && \
    /opt/tomcat/bin/catalina.sh run && \
    /opt/cloudbeaver/cloudbeaver/bin/cloudbeaver && \
    wait
```

</div>