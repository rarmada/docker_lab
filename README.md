## 1. Creando imágenes
#Paso 1.
ejecuta un contenedor basado en la imagen:
```
docker run -it --name miubuntu ubuntu bash
```
Instalo curl
```
apt update 
apt install curl
curl --version
```

<img width="499" height="323" alt="image" src="https://github.com/user-attachments/assets/c5c85bfa-9eba-4700-8a31-8f3db0cbea68" />


# Pregunta
¿Con qué comando podrías guardar los cambios del contenedor como una nueva imagen?

docker commit miubuntu ubuntu-curl

<img width="1136" height="222" alt="image" src="https://github.com/user-attachments/assets/4dc1d4bd-6836-42f8-8c99-d5f13c48e304" />


#PASO 2. Dockerfile
Creamos el archivo Dockerfile
```
 notepad Dockerfile
     FROM ubuntu
     RUN apt-get update && apt-get install -y curl
```
 Contruimos la imagen
```
  docker build -t ubuntu-curl-v2 .
```

<img width="1085" height="395" alt="image" src="https://github.com/user-attachments/assets/95e40750-9171-4f4e-a5e9-17f247b5fa56" />

Ejecutar el contenedor y comprobar curl

<img width="1099" height="188" alt="image" src="https://github.com/user-attachments/assets/ca7dcf22-9fab-454d-8187-521da5c0e851" />

## 3. Volúmenes persistentes
Montar el volumen y correr el contenedor
```
docker volume create datos_postgres
docker run -d --name bdtarea3 --mount type=volume,source=datos_postgres,target=/var/lib/postgresql -e POSTGRES_USER=rafael -e POSTGRES_PASSWORD=1234  -e POSTGRES_DB=mitarea   postgres
docker exec -it bdtarea3 psql -U rafael -d mitarea
```
Crear la tabla e insertar datos
<img width="1131" height="338" alt="image" src="https://github.com/user-attachments/assets/0aa82d2a-455a-4f4e-a68e-742eb25a9ab9" />

###Comprobación
Para el contenedor
```
docker stop bdtarea3
```
Elimina el contenedor
```
docker rm bdtarea3
```
Crea un nuevo contenedor usando el mismo volumen
```
docker run -d  --name bdtarea3-comprobacion   --mount type=volume,source=datos_postgres,target=/var/lib/postgresql   -e POSTGRES_USER=rafael   -e POSTGRES_PASSWORD=1234   -e POSTGRES_DB=mitarea   postgres
docker exec -it bdtarea3-comprobacion psql -U rafael -d mitarea
```
<img width="711" height="226" alt="image" src="https://github.com/user-attachments/assets/c1f8c772-0f73-4941-a757-6e1a56ec460d" />

<img width="638" height="209" alt="image" src="https://github.com/user-attachments/assets/95fb7fbf-e2d2-4535-a4c2-3f90bb546e3b" />

# 4. Bind mounts
Crea un archivo en tu máquina index.html con el contenido <h1>Hola Docker</h1>
docker run -d --name nginx-tarea -p 80:80 --mount type=bind,source=C:\Users\rafaarmada\cursodevops\contenedores\index.html,target=/usr/share/nginx/html/index.html nginx
<img width="607" height="265" alt="image" src="https://github.com/user-attachments/assets/1fb010e7-bde8-4d79-bf1f-6ca58853ae1f" />

##Pregunta:

¿Qué ocurre si modificas el archivo index.html en tu máquina?
al modificar index.html y recargar la página esta aparece con la modificación realizada

# 6. Red 
##Crea una red llamada my-net

docker network create my-net
<img width="1435" height="150" alt="image" src="https://github.com/user-attachments/assets/19dd3c0b-b04d-4b51-9813-af7c94e06402" />

## Arranca dos contenedores ubuntu en esa red.
Instala ping si es necesario.

Arrancamos el primer contenedor
 sudo docker run -it --name ubuntu-ej61 --network my-net ubuntu bash
<img width="2087" height="388" alt="image" src="https://github.com/user-attachments/assets/482919b2-9521-4bb3-9dcd-bb64067f0963" />
Instalo ping apt update && apt install -y iputils-ping

Arrancamos el segundo contenedor
 sudo docker run -it --name ubuntu-ej62 --network my-net ubuntu bash
<img width="2125" height="296" alt="image" src="https://github.com/user-attachments/assets/a128f3bc-daa8-4cc1-867c-0a7b26c0b8bc" />

## Desde un contenedor intenta hacer:
Para averiguar las ips usamos
sudo docker network inspect my-net
<img width="2009" height="1857" alt="image" src="https://github.com/user-attachments/assets/fc8754e8-f037-48d9-931d-13c8c92e8d6f" />

<img width="1326" height="510" alt="image" src="https://github.com/user-attachments/assets/0b3ed29f-9750-4819-87bf-8af5ba708d2e" />

<img width="1308" height="436" alt="image" src="https://github.com/user-attachments/assets/988282b9-4eec-4d7a-8ffb-e1e47aab82ee" />

##Pregunta
¿Los contenedores pueden comunicarse entre sí?

Si se pueden comunicar entre si

# 9. Docker Compose --- Compartiendo volúmenes
Crea un fichero:

docker-compose.yml
 
Con dos servicios.
writer
Debe:
 montar un volumen en /app/logs
 escribir un timestamp cada 30 segundos
reader
Debe:
 montar el volumen en modo solo lectura
 mostrar el contenido en consola


<img width="1079" height="883" alt="image" src="https://github.com/user-attachments/assets/e3226415-4a60-41ab-ab59-7dfb17a1836a" />

Con docker compose up  levantamos los servicios 
<img width="1276" height="437" alt="image" src="https://github.com/user-attachments/assets/cd40b5b8-0fc5-4aff-88f7-76122f4d02b6" />
sudo docker compose ps

<img width="2170" height="284" alt="image" src="https://github.com/user-attachments/assets/3883cb2b-195e-41d8-8f24-c2f54ca1845c" />

    
