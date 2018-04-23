# Estrutura e execução do projeto (BACKEND)

## 1. Estrutura do Dockerfile
Foi criado um arquivo **Dockerfile** na pasta "php-sample-app/backend". Neste arquivo é possível encontrar os comandos de instrução usados para criar um build de uma imagem do Docker e também executar instâncias de containers.

#### 1.1 O Dockerfile do "php-sample-app/backend"

Imagem utilizada para base. Utilizando a ultima versao
> **FROM mysql:5.7**

Copia tudo do diretório corrente
> **COPY ./demo.sql /docker-entrypoint-initdb.d/**

## 2. Pull da imagem do PHP com Apache e MYSQL

Utilizando o Docker CLI, iremos fazer o pull da imagem do PHP com Apache e do MYSQL. **Já no diretório do "backend"**, execute os seguintes comandos:

Pull da imagem do PHP com o Apache

> **docker pull php:7.2-apache**

Pull da imagem do MYSQL em sua última versão

> **docker pull mysql:latest**

## 3. Build da imagem do MYSQL

Uma imagem Docker são blocos de containers em execução.
Para executar um container é preciso construir a imagem inicialmente.

Comando para o build da imagem. O "-t" é a tag ou nome da imagem e os números após os ":" é a versão da imagem.

> **docker build . -t db:0.0.1**

Para verificar as imagens criadas, utilize:

> **docker images**

Agora está tudo pronto para executar a aplicação com o MYSQL utilizando um container baseado na aplicação da imagem que foi criada. Detalhes do comando: o "-d" executa o container em segundo plano, ou seja, o trabalho feito não ocupará o terminal; o "-e" indica o uso de variável; "MYSQL_DATABASE=demo" é o nome do BD; "MYSQL_ALLOW_EMPTY_PASSWORD=yes" permite o uso de senha vazia e "--name" nome do BD.

> **docker run -d -e MYSQL_DATABASE=demo -e MYSQL_ALLOW_EMPTY_PASSWORD=yes --name backend db:0.0.1**

Para verificar se o BD tem tudo necessário, execute:
Detalhes do comando: estamos executando um comando no container que está sendo executado e o "mysql -u root -p" conecta no banco.

> **docker exec -ti backend mysql -u root -p**

## 4. Criar a comunicação entre o backend e o frontend

O Build

> **docker build . -t frontend:0.0.1**

Fazer a comunicação entre o backend e o frontend

> **docker run -d -p 80:80 --name frontend --link backend frontend:0.0.1**
