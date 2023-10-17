---
title: "Criação das demais entidades simples"
permalink: /primeiros-passos/outras-entidades-simples
---

# Criação das demais entidades simples

Ao olharmos o diagrama de entidade e relacionamento, podemos identificar algumas entidades simples, que possuem apenas atributos simples, sem relacionamentos com outras entidades. São elas:

* Categoria (já criada)
* Pais
* TipoAtuacao

 Para manter um padrão de desenvolvimento, não usaremos acentos ou cedilhas na nomenclatura das entidades e atributos.

## Criando os modelos

Vamos criar os modelos das entidades `Pais` e `TipoAtuacao`. Abra o arquivo `core/models.py` e adicione o seguinte código:

```python
class Pais(models.Model):
    nome = models.CharField(max_length=60)

    def __str__(self):
        return self.nome


class TipoAtuacao(models.Model):
    descricao = models.CharField(max_length=100)

    def __str__(self):
        return self.descricao
```

## Criando e executando as migrações

Agora que criamos os modelos, precisamos criar as migrações. Para isso, digite o seguinte comando no terminal:

```bash
python manage.py makemigrations
```

Esse comando criará as migrações necessárias para criar as tabelas no banco de dados. Para executar as migrações, digite o seguinte comando no terminal:

```bash
python manage.py migrate
```

## Registrando os modelos no admin

Para que os modelos sejam exibidos no sistema de administração, é preciso registrá-los no arquivo `core/admin.py`. Abra o arquivo `core/admin.py` e adicione o seguinte código:

```python
from django.contrib import admin

from .models import Categoria, Pais, TipoAtuacao

admin.site.register(Categoria)
admin.site.register(Pais)
admin.site.register(TipoAtuacao)
```

Note que apenas importamos as classes `Pais` e `TipoAtuacao` e as registramos no sistema de administração.

Para visualizar os modelos no sistema de administração, basta acessar o sistema de administração no navegador. Não esqueça o servidor de desenvolvimento deve estar em execução. Para iniciar o servidor de desenvolvimento, digite o seguinte comando no terminal:

```bash
python manage.py runserver
```

# Conclusão da aula

Nesta aula, aprendemos a criar os modelos das entidades simples do sistema e a registrá-los no sistema de administração. Na próxima aula, aprenderemos a criar os modelos das entidades com relacionamentos.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Criação do App e primeiro modelo](criacao-do-app "Anterior")</span>
<span> 
[Sumário &gt;](../ "Início")  </span></span>