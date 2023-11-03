# TALLER DE INTRODUCCIÓN A VIRTUALIZACIÓN Y PROG. DISTRIBUIDA
## María José Torres Nieves

En este taller se profundizaron los conceptos de documentación de diseño en artefactos de software, cloud y virtualización usando Docker y AWS, gracias a que consiste en crear una aplicación web sencilla soportada en el micro-framework de Spark de java, la cual fue dockerizada y desplegada en una máquina virtual de AWS.

Lo anterior se puede visualizar en la siguiente imagen:
![Modelo](/evidencia/modelo.png)

Para lograr esto, se dividió el trabajo en cuatro partes:

1. Creación aplicación web
2. Creación imagen
3. Subir imagen
4. Despliegue en la nube

A lo largo de este README, se explicará y evidenciará lo logrado.

## Primera Parte

Para iniciar se creó un proyecto Java usando Maven. Al ser una aplicación web simple solo se usó una clase (principal) con el micro-framework Spark para realizar un servidor web que escucha un puerto configurado a través de la variable **"PORT"**. Este servidor responde un “Hello Docker!” cuando la ruta es "/hello". Al usar Maven , se debe instalar las dependencias necesarias para el correcto funcionamiento del servidor.

![Evidencia 1](/evidencia/ev1.png)
![Evidencia 2](/evidencia/ev2.png)

Se realizo una verificación del correcto funcionamiento del servidor localmente:

![Evidencia 3](/evidencia/ev3.png)

## Segunda Parte

Al confirmar que el servidor funciona, se inició la dockerización con el archivo Dockerfile y el comando docker build --tag dockersparkprimer . para construir la imagen:

![Evidencia 4](/evidencia/ev4.png)
![Evidencia 5](/evidencia/ev5.png)

Con la imagen, se crearon tres instancias de un contenedor Docker independientes:

![Evidencia 6](/evidencia/ev6.png)
![Evidencia 7](/evidencia/ev7.png)
![Evidencia 8](/evidencia/ev8.png)
![Evidencia 9](/evidencia/ev9.png)

Además, se usó Docker-compose con el fin de generar automáticamente la configuración Docker:

![Evidencia 10](/evidencia/ev10.png)
![Evidencia 11](/evidencia/ev11.png)

## Tercera Parte

En mi cuenta de DockerHub, se creó un repositorio y una referencia a la imagen previamente creada con el nombre de este repositorio:

![Evidencia 12](/evidencia/ev12.png)

Después del proceso de autenticación, se subió la imagen a DockerHub:

![Evidencia 13](/evidencia/ev13.png)

## Cuarta Parte

Para esta parte se creó una máquina virtual EC2 de AWS a la cual se le instaló Docker para iniciar su servicio:

![Evidencia 14](/evidencia/ev14.png)
![Evidencia 15](/evidencia/ev15.png)

Después se creó una instancia de un contenedor Docker con lo subido al repositorio de DockerHub:

![Evidencia 16](/evidencia/ev16.png)

También se habilitaron los puertos necesarios de la máquina para que responda el servidor:

![Evidencia 17](/evidencia/ev17.png)

Con todo lo anterior finalizado, se hizo el llamado al servicio y se obtuvo el siguiente resultado:

![Evidencia 18](/evidencia/ev18.png)

## Resumen

En resumen, en este taller se documentó y demostró la creación de una sencilla aplicación web Java utilizando Spark, su contenerización en Docker, carga en DockerHub y despliegue en una máquina virtual de AWS, habilitando el acceso a la aplicación a través de la nube.
