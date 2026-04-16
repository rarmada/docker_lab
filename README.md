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

