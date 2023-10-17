---
title: "Criação do primeiro app"
permalink: /primeiros-passos/criacao-do-app
---

# Criando o primeiro app

Para criar o primeiro app, digite o seguinte comando no terminal (com o ambiente virtual habilitado):

```bash
python manage.py startapp core
```

Isso criará um diretório chamado `core` com os arquivos do app. O diretório `core` contém os seguintes arquivos:

* `core/`: diretório com os arquivos do app
* `core/__init__.py`: arquivo vazio que indica que o diretório `core` é um pacote Python
* `core/admin.py`: arquivo com as configurações do sistema de administração do app
* `core/apps.py`: arquivo com as configurações do app
* `core/migrations/`: diretório com as migrações do app
* `core/models.py`: arquivo com os modelos de dados do app
* `core/tests.py`: arquivo com os testes do app
* `core/views.py`: arquivo com as views do app

Neste curso não iremos nos deter com todos os arquivos, mas apenas alguns deles, em especial o arquivo `core/models.py`, que contém os modelos de dados do app, e o arquivo `core/admin.py`, que contém as configurações do sistema de administração do app.

## Registrando o app no projeto

Para que o Django reconheça o app, é preciso registrá-lo no arquivo `config/settings.py`. Para isso, abra o arquivo `config/settings.py` e localize a variável `INSTALLED_APPS`. Essa variável contém a lista de apps instalados no projeto. Adicione o nome do app `core` ao final da lista:

```python
INSTALLED_APPS = [
    # ...
    'core',
]
```

## Criando o primeiro modelo