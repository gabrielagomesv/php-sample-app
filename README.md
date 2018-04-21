# Sistemas para Internet - SecDevOps

***nac:*** Criação de uma aplicação no formato "CRUD" executada em containers com base na linguagem "PHP" e no banco de dados "MySQL";

---

***Importante:***

Instruções sobre modelo de execução e entregáveis podem ser obtidas no [diretório de documentação](https://github.com/fiapsecdevops/php-sample-app/tree/master/docs) ou no portal do aluno;

Duvidas podem ser enviadas para <profhelder.pereira@fiap.com.br>

Esta app foi adaptada do exemplo contido [neste artigo](https://www.tutorialrepublic.com/php-tutorial/php-mysql-crud-application.php)

A estrutura foi criada com base nas seguintes tags:

- frontend-0.1: Versão de testes SEM conexão com o banco para a primeira parte da NAC;
- stable:  Versão COM as linhas de conexão com o banco configuradas, será necessário que o MySQL esteja operante para testes faltando apenas a criação do Dockerfile da aplicação/mysql;

---

## Execução do projeto

Para entendimento individual e completo de toda a aplicação criada. Separei os comandos nos "README.md" de cada parte da aplicação. 

No diretório "frontend" há um "README.md" explicando como foi feito a montagem do Dockerfile, como é feito o build da imagem e a execução.

No diretório "backend" há um "README.md" explicando como foi feito a montagem do Dockerfile, o pull da imagem do PHP com Apache e do MYSQL, como é feito o build da imagem do MYSQL, a exeução da aplicação e a criação da comunicação entre o backend e o frontend. 

**Para execução completa da aplicação, recomendo a leitura e a aplicação começando inicialmente pelo frontend e depois o backend, pois está em ordem de execução até o momento que a comunicação entre os dois é criada.** 

#### 1. Execução dos containers de frontend e backend

> **1. [Frontend](https://github.com/gabrielagomesv/php-sample-app/blob/master/frontend/README.md)**

> **2. [Backend e comunicação entre os containers](https://github.com/gabrielagomesv/php-sample-app/blob/master/backend/README.md)**

#### 2. Componentes

**demo.sql**

O arquivo "demo.sql" trata-se do script SQL que irá criar o banco da aplicação.
A construção da aplicação para o BD foi criada seguindo o conceio do **Stateful**, ou seja, essa construção busca encontrar a melhor forma de executar o container que necessita de um local para armazenagem de seus dados.

Em contrapartida, nosso frontend seguiu o conceito **Stateless**, ou seja, não há retenção de informação e quando o container é necessário é preciso criar seu build.
