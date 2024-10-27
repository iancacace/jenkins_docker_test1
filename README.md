# jenkins_docker
Ejemplo de generación de imagen docker desde Jenkins
# para la dockerfile de la construccion de la imagen de jenkins se utilizo:
# FROM jenkins/jenkins:lts-jdk17
# USER root
# RUN apt-get update && apt-get install -y curl \ #se instala el docker client en el conteiner donde se usara jenkins.
 #   && curl -sSL https://get.docker.com/ | sh \
 #   && groupadd -g 1001 docker_host \  #creamos el grupo 1001 con el nombre Docker_host
  #  && usermod -aG docker_host jenkins  #añadimos el user Jenkins a este grupo
# USER Jenkins
