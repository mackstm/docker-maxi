<div align="justify">

# Instalación de Apache Tomcat a través de Docker

## Índice

- [Preparación del entorno](#index01)
- [Descargar la imagen de Tomcat](#index02)
- [Ejecutar el contenedor de Tomcat](#index03)
- [Probar la Configuración](#index04)
- [Detener y eliminar el contenedor](#index05)
- [Verificación en otro puerto](#index06)

### Preparación del entorno <a name="index01"></a>

<img src="img/img01.png"/>

### Descargar la imagen de Tomcat <a name="index02"></a>

<img src="img/img02.png"/>

Y al ejecutar docker images:

<img src="img/img03.png"/>

### Ejecutar el contenedor de Tomcat <a name="index03"></a>

<img src="img/img04.png"/>

### Probar la configuración <a name="index04"></a>

Al acceder a localhost:9090, nos encontramos con:

<img src="img/img05.png"/>

Esto es normal, ya que no tenemos ninguna aplicación arrancada aún en apache. El contenedor en sí funciona, que es lo que nos interesa por ahora.

<img src="img/img06.png"/>

<img src="img/img07.png"/>

### Detener y eliminar el contenedor <a name="index05"></a>

<img src="img/img08.png"/>

### Verificación en otro puerto <a name="index06"></a>

Probamos que funciona todo en el puerto 9001:

<img src="img/img09.png"/>

<img src="img/img10.png"/>

</div>