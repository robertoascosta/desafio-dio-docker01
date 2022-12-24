#Readme de criação de um container de uma aplicação WEB

#Verigficar VM do Linux Server, fazer conexão ssh através do putty

#Instalação do Docker de forma mais pratica

curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh

#Verificando a versão e os status do Docker

docker version
systemctl status docker

#instalar servidor apache2 para uso WEB

docker pull httpd

#Verificar a imagem Apache no docker

docker images

#Rodar imagem Apache refereciando porta de conexão, especificando caminho e imagem

docker run --name apache-A -d -p 80:80 --volume=/home/osboxes/docker/apache-A:/usr/local/apache2/htdocs httpd

#instandlo do docker-compose em sua maquina linux

apt install docker-compose -y

#Criar um arquivo yml com os parâmetros, e criar html na pasta referente ao docker para diferenciar no index

#Criação do arquivo YML

version: '3.9'
services:
  apache:
    image: httpd:latest
    container_name: my-apache-app
    ports:
    - '80:80'
    volumes:
    - ./website:/usr/local/apache2/htdocs

#Criação do index refencial ao desafio

nano index.html

#Usar o docker-compose para gerar o arquivo e checar uma pagina com IP para visualizar o index

docker-compose up -d