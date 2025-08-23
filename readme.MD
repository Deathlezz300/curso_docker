<!--
tags: docker, comandos, contenedores, imágenes, tutorial, cheatsheet, devops, docker-hub
-->
Comandos docker

docker pull 'name' por defecto la tomará de docker hub a menos que se especifique otro
docker container run 'nombre_imagen' -  esto sirve para crear un contenedor de docker apartir de una imagen
docker container --help - sirve para ver todos los comandos que se pueden ejecuttar en el contexto de los comandos de los contenedores

docker container ls -a - el '-a' al final sirve para listar absolutamente todos los contenedores,estén estos corriendo o no

docker container rm 'id or container name' , puede remover un contenedor o varios contenedores

docker container prune -  elimina todos los contenedores de docker


docker image --help para obtener la list de los comandos disponibles que hay sobre images de docker


docker image rm 'image_name' para eliminar una imagen en concreto

