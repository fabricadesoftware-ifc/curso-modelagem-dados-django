---
title: "Primeira migração e criação do admin"
permalink: /primeiros-passos/primeira-migracao
---

# Primeira migração e criação do admin

## Executando a primeira migração

Para que o Django crie as tabelas no banco de dados, é preciso executar a primeira migração. Note que ao criar um projeto, o Django já cria uma migração inicial, que cria as tabelas necessárias para o sistema de autenticação de usuários. Para executar a primeira migração, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
python manage.py migrate
```

Ao executar esse comando, o Django criará o banco de dados para o projeto, que no nosso caso está usando o SQLite, e criará as tabelas necessárias para o sistema de autenticação de usuários. Note que foi criado um arquivo chamado `db.sqlite3`, que é o banco de dados do projeto.

Podemos agora abrir esse arquivo com o visualizador de banco de dados do VSCode. Para isso, clique duas vezes no arquivo `db.sqlite3` no VSCode. Isso abrirá o visualizador de banco de dados do VSCode, que permite visualizar as tabelas do banco de dados e executar comandos SQL. 

## Criando o superusuário

Para criar o superusuário, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
python manage.py createsuperuser
```

Isso abrirá um assistente para a criação do superusuário. Digite o nome de usuário, e-mail e senha do superusuário. Após digitar os dados, pressione a tecla `Enter` para confirmar cada dado. Ao final, o superusuário será criado.

## Confirmando a criação do usuário no banco de dados

Podemos agora confirmar que o superusuário foi criado no banco de dados. Para isso, abra o arquivo `db.sqlite3` no visualizador de banco de dados do VSCode. Procure pela tabela `auth_user` e note que o usuário foi criado com o nome de usuário, e-mail e senha que você digitou no assistente.

## Testando o sistema de administração

Podemos agora testar o sistema de administração. Para isso, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
python manage.py runserver
```

Isso iniciará o servidor de desenvolvimento do Django. Abra o navegador e digite a URL `http://localhost:8000/admin`. Isso abrirá a tela de login do sistema de administração. Digite o nome de usuário e senha do superusuário que você criou anteriormente. Isso abrirá a tela do sistema de administração do Django.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. "Início")</span>
<span> 
[Criação do primeiro app &gt;](criacao-do-app "Próximo")  </span></span>