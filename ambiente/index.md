---
title: "Preparação do ambiente de desenvolvimento"
description: Configuração do ambiente de desenvolvimento no Linux
permalink: /ambiente
---

# Preparação do ambiente

## Pré-requisitos

Estamos considerando o uso do sistema operacional Linux, com a distribuição Ubuntu, embora o Django possa ser usado em outros sistemas operacionais. Também estamos considerando que o Python 3 já está instalado no sistema operacional com o gerenciador `pip`. Também usaremos o editor de texto [Visual Studio Code](https://code.visualstudio.com/).

## Instalação dos pacotes necessários

Usaremos neste curso o banco de dados SQLite. Embora o Django possa ser usado com outros bancos de dados, o SQLite é o mais simples de instalar e usar. Embora não seja necessário instalar nada adicional para que o Django possa manipular os dados com SQLite, instalaremos um cliente para que possamos visualizar e manipular os dados posteriormente. Para instalar o SQLite, digite o seguinte comando no terminal:

```bash
sudo apt install sqlite3
```

Também instalaremos uma extensão para visualizar os dados do SQLite no Visual Studio Code. Para isso, abra o Visual Studio Code e digite `Ctrl+Shift+X` para abrir a lista de extensões. Digite `SQLite` na caixa de busca e instale a extensão `SQLite Viewer`. 

## O projeto do curso

Vamos criar um projeto Django para o curso. Para isso, vamos criar uma pasta (diretório) para o projeto do curso. Nesse caso, vamos considerar que a pasta do projeto se chama `minicurso-django`, e abrir essa pasta no Visual Studio Code. Para abrir a pasta no Visual Studio Code. 

Neste curso, vamos modelar um sistema para gerenciamento de filmes.

### Criando um ambiente virtual

O ambiente virtual é uma forma de isolar as dependências de cada projeto. Isso permite que cada projeto tenha suas próprias dependências, sem interferir nas dependências de outros projetos. Para criar um ambiente virtual, digite o seguinte comando no terminal (dentro da pasta do projeto):

```bash
python3 -m venv venv
```

Isso criará um diretório chamado `venv` com o ambiente virtual. Para ativar o ambiente virtual, digite o seguinte comando no terminal:

```bash
source venv/bin/activate
```

O nome do ambiente virtual aparecerá no início da linha de comando, indicando que o ambiente virtual está ativo. Se você quiser sair do ambiente virtual, digite o seguinte comando no terminal:

```bash
deactivate
```

 Importante: não execute esse comando agora, pois precisamos do ambiente virtual ativo para instalar as dependências do projeto.

### Instalando o Django

Para instalar o Django, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
pip install django
```

### Criando o projeto

Para criar o projeto, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
django-admin startproject config .
```

Isso criará um diretório chamado `config` com os arquivos do projeto. O ponto no final do comando indica que o projeto deve ser criado no diretório atual. O diretório atual, além da pasta `venv` contém os seguintes arquivos:

* `manage.py`: script para executar comandos do Django
* `config/`: diretório com as configurações do projeto
* `config/__init__.py`: arquivo vazio que indica que o diretório `config` é um pacote Python
* `config/settings.py`: arquivo com as configurações do projeto
* `config/urls.py`: arquivo com as rotas do projeto
* `config/asgi.py`: arquivo com as configurações do projeto para o ASGI
* `config/wsgi.py`: arquivo com as configurações do projeto para o WSGI

### Executando o servidor de desenvolvimento

Para executar o servidor de desenvolvimento, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
python manage.py runserver
```

Ao executar esse comando, você verá um tela como esta:

 Performing system checks...
 
 System check identified no issues (0 silenced).
 
 You have unapplied migrations; your app may not work properly until they are applied.
 Run 'python manage.py migrate' to apply them.
 
 outubro 17, 2023 - 08:00:00
 Django version 4.2, using settings 'config.settings'
 Starting development server at http://127.0.0.1:8000/
 Quit the server with CONTROL-C.

Isso iniciará o servidor de desenvolvimento na porta 8000. Para acessar o servidor de desenvolvimento, abra o navegador e digite a URL `http://localhost:8000`. Você verá uma página com a mensagem "The install worked successfully! Congratulations!". Para parar o servidor de desenvolvimento, digite `Ctrl+C` no terminal.

Note também que foram apresentados alguns avisos sobre migrações não aplicadas. Vamos ignorar esses avisos por enquanto, e vamos aplicar as migrações mais tarde.

#### Alterando a porta do servidor de desenvolvimento

Se você quiser alterar a porta do servidor de desenvolvimento, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
python manage.py runserver 8080
```

Isso iniciará o servidor de desenvolvimento na porta 8080. Para acessar o servidor de desenvolvimento, abra o navegador e digite a URL `http://localhost:8080`.

Se você quiser alterar o endereço do servidor de desenvolvimento, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
python manage.py runserver 0.0.0.0:8000
```

Nesse caso, o servidor de desenvolvimento será iniciado na porta 8000, mas poderá ser acessado de qualquer endereço IP que o seu computador estiver usando no momento. Para acessar o servidor de desenvolvimento, abra o navegador e digite a URL `http://<endereço IP>:8000`.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. "Início")</span>
<span></span></span>