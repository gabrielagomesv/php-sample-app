# De onde esta vindo a imagem PHP e qual a versão utilizada.
FROM php:7.2-apache

# Instalando extensoes do php
# Permite o mysqli conectar com o BD
RUN docker-php-ext-install mysqli

# Diretorio de execucao da aplicacao
WORKDIR /var/www/html/

# Copia o conteudo PHP todo que esta neste diretorio para a web 
COPY . /var/www/html/

