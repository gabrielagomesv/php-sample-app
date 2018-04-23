# Estrutura e execução do projeto (FRONTEND)

## 1. Estrutura do Dockerfile

Foi criado um arquivo **Dockerfile** na pasta "php-sample-app/frontend". Neste arquivo é possível encontrar os comandos de instrução usados para criar um build de uma imagem do Docker e também executar instâncias de containers.

#### 1.1 O Dockerfile do "php-sample-app/frontend"

De onde esta vindo a imagem PHP.

> **FROM php:7.2-apache**

Instalando extensões do php. Permite o mysqli conectar com o BD.

> **RUN docker-php-ext-install mysqli**

Diretório de execução da aplicação.

> **WORKDIR /var/www/html/**

Copia o conteudo PHP todo que esta neste diretório para a web.

> **COPY . /var/www/html/**

---

## 2. Build da imagem "php-sample-app/frontend"

Uma imagem Docker são blocos de containers em execução.
Para executar um container é preciso construir a imagem inicialmente.

#### 2.1 Comandos

Observações: os comandos a seguir devem ser feitos utilizando o Docker CLI e **você deve estar no diretório do Frontend**.

O primeiro trata-se da build da imagem. O "-t" é a tag ou nome que foi dado a imagem e"frontend-php" é o nome que escolhemos para ela. Os números após os ":" é a versão da imagem.

> **docker build . -t frontend-php:0.0.1**

Para verificar se realmente a imagem foi criada, você pode utilizar o comando:

> **docker images**

Agora, está tudo pronto para executar a aplicação com o Apache utilizando um container baseado na aplicação da imagem que foi criada/"buildada". Detalhes do comando: o "-d" deixa o container executando em segundo plano, "-p" mostra a porta utilizada, "--rm --name" é o nome do container
Para executar, utiliza o comando:

> **docker run -d -p 80:80 --rm --name frontend frontend-php:0.0.1**

**Para verificar se houve sucesso na execução, acesse o endereço localhost (caso seja windows): **http://192.168.99.100/**

Para ver o container em execução você pode utilizar o comando Docker CLI:

> **docker ps**
