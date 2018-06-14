# examen 2
Examen del curso básico de microservicios

-----------------------------------------------------------------------------------------------------------------------------------

Compilar examen 2

 docker run -it -v /home/gustavo/curso-dgpe/examen2/:/codigo kebblar/jdk18-utf8-debug-maven mvn -f /codigo clean package

Levantar la vertical

docker run -d -p 6060:8080 -v /home/gustavo/curso-dgpe/examen2/:/codigo kebblar/jdk18-utf8-debug-maven java -jar /codigo/target/sample-1.0-SNAPSHOT-fat.jar

Ruta

http://192.168.1.155:6060/api/cuenta?mode=6

Crear Dockerfile en el proyecto del vector

Dockerfile


################################################################################
FROM kebblar/jdk18-utf8-debug-maven
COPY ./target/sample-1.0-SNAPSHOT-fat.jar /javabin/sample-1.0-SNAPSHOT-fat.jar
CMD java -jar /javabin/sample-1.0-SNAPSHOT-fat.jar
################################################################################


Dockerizar vector
docker build -t examen2 .

Correr imagen Docker creada
docker run -it -d -p 4070:8080 examen2

Verificar id del docker
Docker ps

Commit del docker

docker commit 4a83c3d20f9c dgpecurso11/examen2

Rutas del proyecto examen2

https://github.com/dgpecurso11/examen2

https://hub.docker.com/r/dgpecurso11/examen2


Instalar rancher para escalarlo a tres servidores 


$ sudo docker run -d --restart=unless-stopped -p 8080:8080 rancher/server:stable


Creando el servicio del API en rancher

Agregamos el nombre, descripción e imagen.

Ruta del docker hub: 

https://hub.docker.com/r/dgpecurso11/examen2
Nombre de la imagen:

dgpecurso11/examen2


Despues agregamos 3 imagenes en puertos distintos del servicio del vector,  por ejemplo 8085,8086 y 8087
