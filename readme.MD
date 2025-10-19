<!--
tags: docker, comandos, contenedores, imágenes, tutorial, cheatsheet, devops, docker-hub
-->
Comandos docker

docker pull 'name' por defecto la tomará de docker hub a menos que se especifique otro  - descargar la imagen
docker container run 'nombre_imagen' -  esto sirve para crear un contenedor de docker apartir de una imagen
docker container --help - sirve para ver todos los comandos que se pueden ejecuttar en el contexto de los comandos de los contenedores

docker container ls -a - el '-a' al final sirve para listar absolutamente todos los contenedores,estén estos corriendo o no

docker container rm 'id or container name' , puede remover un contenedor o varios contenedores

docker container prune -  elimina todos los contenedores de docker


docker image --help para obtener la list de los comandos disponibles que hay sobre images de docker


docker image rm 'image_name' para eliminar una imagen en concreto

docker container run -d -p:80:80 'image_name' - esto sirve para levantar una imagen de docker en el puerto 80:80

Crear container de postgres -- docker container run --name test-postgres -dp 5432:5432 -e POSTGRES_PASSWORD=mysecretpassword postgres


--Escribir por lineas el comando en la terminal con '\' en powershell con  '`'

docker container run `
--name postgres-alpha `
-e POSTGRES_PASSWORD=pass_test_at `
-dp 5432:5432 `
postgres

docker container run `
--name world-db `
-e MARIADB_USER=example-user `
-e MARIADB_PASSWORD=user-password `
-e MARIADB_ROOT_PASSWORD=root-secret-password `
-e MARIADB_DATABASE=world-db `
-dp 3306:3306 `
mariadb:10.11.14-jammy

#Ahora vamos a usar volumenes

docker container run `
--name world-db `
-e MARIADB_USER=example-user `
-e MARIADB_PASSWORD=user-password `
-e MARIADB_ROOT_PASSWORD=root-secret-password `
-e MARIADB_DATABASE=world-db `
-dp 3306:3306 `
-v world-db:/var/lib/mysql `
mariadb:10.11.14-jammy

#Networks section

#Para que dos conectendores o mas se puedan comunicar entre si estos deben estar metidos en una misma network

docker network create world-app

docker network connect world-app 0a3

docker network connect world-app ab0

#Comando para phpMyAdmin
docker container run `
--name phpmyadmin `
-d `
-e PMA_ARBITRARY=1 `
-p 8080:80 `
phpmyadmin:5.2.0-apache

#Inicializar instancias de ambos contenedores conectadonlos directamente a la misma network

docker container run `
--name world-db `
-e MARIADB_USER=example-user `
-e MARIADB_PASSWORD=user-password `
-e MARIADB_ROOT_PASSWORD=root-secret-password `
-e MARIADB_DATABASE=world-db `
-dp 3306:3306 `
-v world-db:/var/lib/mysql `
--network world-app `
mariadb:10.11.14-jammy

docker container run `
--name phpmyadmin `
-d `
-e PMA_ARBITRARY=1 `
-p 8080:80 `
--network world-app `
phpmyadmin:5.2.0-apache

#Binds section

docker run `
--name nest-app `
-w /app `
-p 80:3000 `
-v "${PWD}:/app" `
node:16-alpine3.16 `
sh -c "npm install && npm run start:dev"

#Este comando sirve para ver los logs de los contenedores
docker container logs -f

#Ejecutar terminal interactiva

docker exec -it "container_id" /bin/sh

cat - imprimir la información en la consola de la terminal interactiva
