docker pull jllorente/javaapp
docker run --name prueba -it --rm jllorente/javaapp java -jar PrivaliaSpringProject-0.0.1-SNAPSHOT.jar

Aquí lo tienes:

Crear un docker para ejecutar un .jar:

1.- Generar .jar
mvn clean package

 Dentro de la carpeta tarjet:
java -jar PrivaliaSpringProject-0.0.1-SNAPSHOT.jar

2.-Crear fichero Dockerfile

FROM java:8
ADD ./dist/PrivaliaSpringProject-0.0.1-SNAPSHOT.jar PrivaliaSpringProject-0.0.1-SNAPSHOT.jar
ADD ./dist/lib lib
EXPOSE 8080
CMD java -jar PrivaliaSpringProject-0.0.1-SNAPSHOT.jar
MAINTAINER "David Becerra <david.becerra@avanttic.com>"

3.- Crear imagen docker

  docker build -t dbecerra/listasspring .
  
4.-Docker Push, subir imagen al repositorio
  docker push dbecerra/listasspring