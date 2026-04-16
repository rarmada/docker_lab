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
docker run -d --name bdtarea3  --mount type=bind,source=C:\Users\rafaa\cursodevops\bbdd,target=/var/lib/postgresql  -e POSTGRES_USER=rafael  -e POSTGRES_PASSWORD=1234   -e POSTGRES_DB=mitarea   postgres
```

Verificar que esta corriendo
```
docker ps
```
entrar en el contenedor
```
docker exec -it bdtarea3 psql -U rafael -d mitarea
```
<img width="481" height="142" alt="image" src="https://github.com/user-attachments/assets/8fc4641d-494a-4b14-856e-27930a4ec44e" />


<img width="749" height="123" alt="image" src="https://github.com/user-attachments/assets/528528b8-5eab-4f52-ac53-b8df8132a0fa" />

###Comprobación
Para el contenedor
```
<img width="514" height="231" alt="image" src="https://github.com/user-attachments/assets/fab9dab0-277a-44b7-a1e2-9bfc7cd7556c" />
```

Elimina el contenedor
```
docker rm bdtarea3
```
Crea un nuevo contenedor usando el mismo volumen
Comprueba que los datos siguen existiendo.

<img width="514" height="231" alt="image" src="https://github.com/user-attachments/assets/071be983-1145-4ed0-b0f1-521bf766f916" />


