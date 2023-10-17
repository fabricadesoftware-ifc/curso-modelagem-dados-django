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

Vamos iniciar criando a primeira entidade, que será a `categoria`. Para isso, abra o arquivo `core/models.py` e adicione o seguinte código:

```python
from django.db import models


class Categoria(models.Model):
    descricao = models.CharField(max_length=40)

    def __str__(self):
        return self.descricao
```

O código acima cria uma classe chamada `Categoria` que herda de `models.Model`. Essa classe representa uma entidade do sistema. A classe `Categoria` possui um atributo chamado `descricao`, que é uma instância de `models.CharField`. Esse atributo representa um campo de texto com no máximo 40 caracteres. O método `__str__` retorna a descrição da categoria.

### Criando a primeira migração

Agora que criamos o primeiro modelo, precisamos criar a primeira migração. Para isso, digite o seguinte comando no terminal:

```bash
python manage.py makemigrations
```

Esse comando irá criar um arquivo de migração no diretório `core/migrations`. O nome do arquivo de migração é gerado automaticamente pelo Django. No nosso caso, o nome do arquivo é `0001_initial.py`. O número `0001` indica que essa é a primeira migração do app. O nome `initial` indica que essa é a migração inicial do app.

Como criamos a classe `Categoria`, o arquivo de migração conterá os códigos necessários para criar a tabela `core_categoria` no banco de dados. Para visualizar o código gerado, abra o arquivo `core/migrations/0001_initial.py` e localize a classe `Migration`. Essa classe contém dois métodos: `dependencies` e `operations`. O método `dependencies` indica as dependências da migração. Como essa é a primeira migração do app, não há dependências. O método `operations` contém as operações que serão executadas no banco de dados. No nosso caso, a operação é a criação da tabela `core_categoria`. 

### Executando a primeira migração

Agora que criamos a primeira migração, precisamos executá-la. Para isso, digite o seguinte comando no terminal:

```bash
python manage.py migrate
```

Esse comando irá executar todas as migrações pendentes. Como resultado, a tabela `core_categoria` será criada no banco de dados.

 Note que o nome `core_categoria` foi gerado automaticamente pelo Django. O nome da tabela é composto pelo nome do app (`core`) e pelo nome da classe (`Categoria`). O Django também adiciona um campo `id` à tabela. Esse campo é a chave primária da tabela e é gerado automaticamente pelo Django. Essas configurações podem ser alteradas, mas não veremos neste momento no curso.

### Adicionando ao sistema de administração

Agora que criamos o modelo `Categoria`, vamos adicioná-lo ao sistema de administração. Para isso, abra o arquivo `core/admin.py` e adicione o seguinte código:

```python
from django.contrib import admin
from .models import Categoria


admin.site.register(Categoria)
```

O código acima importa a classe `Categoria` e a registra no sistema de administração. Agora, abra o navegador e acesse a página de administração do projeto. No nosso caso, a URL é `http://localhost:8000/admin`. Faça o login com o usuário e senha criados anteriormente. 

Agora, você verá uma seção chamada `Core` com o modelo `Categoria`. Clique no modelo `Categoria` para acessar a página de listagem de categorias. Como ainda não temos nenhuma categoria cadastrada, a página estará vazia. Clique no botão `Adicionar categoria` para cadastrar uma nova categoria. Na página de cadastro, digite a descrição da categoria e clique no botão `Salvar`. A categoria será cadastrada e você será redirecionado para a página de listagem de categorias.

### Visualizando a tabela no banco de dados

Agora que cadastramos a primeira categoria, vamos verificar se ela foi cadastrada no banco de dados. Para isso, usando o Visual Studio Code, abra o arquivo `db.sqlite3`, e localize a tabela `core_categoria`.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Primeira migração](primeira-migracao "Anterior")</span>
<span> 
[Outras entidades simples &gt;](outras-entidades-simples "Próximo")  </span></span>