## 1. Creando imágenes
ejecuta un contenedor basado en la imagen:
docker run -it --name miubuntu ubuntu bash
Instalo curl
apt update 
apt install curl
curl --version

<img width="499" height="323" alt="image" src="https://github.com/user-attachments/assets/c5c85bfa-9eba-4700-8a31-8f3db0cbea68" />


# Pregunta
¿Con qué comando podrías guardar los cambios del contenedor como una nueva imagen?

docker commit miubuntu ubuntu-curl

<img width="1136" height="222" alt="image" src="https://github.com/user-attachments/assets/4dc1d4bd-6836-42f8-8c99-d5f13c48e304" />
