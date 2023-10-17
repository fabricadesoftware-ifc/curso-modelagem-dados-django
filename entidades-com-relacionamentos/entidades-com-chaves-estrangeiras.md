---
title: "Entidades com chaves estrangeiras"
permalink: /entidades-com-relacionamentos/entidades-com-chaves-estrangeiras
---

# Criando a entidade Produtora

Vamos começar criando a entidade `Produtora`. Abra o arquivo `core/models.py` e adicione o seguinte código:

```python
class Produtora(models.Model):
    nome = models.CharField(max_length=100)
    pais = models.ForeignKey(Pais, on_delete=models.PROTECT)

    def __str__(self):
        return self.nome
```

No código acima, criamos a entidade `Produtora`, que possui um atributo `nome` e um atributo `pais`. O atributo `pais` é uma referência para a entidade `Pais`. Para isso, usamos o tipo `ForeignKey`, que representa uma chave estrangeira. O parâmetro `on_delete=models.PROTECT` indica que não é possível excluir um país que esteja sendo referenciado por uma produtora. Poderíamos usar outros valores para esse parâmetro, como `CASCADE`, que indica que, ao excluir um país, todas as produtoras que referenciam esse país também serão excluídas.

Em seguida, faremos a migração. Para isso, digite o seguinte comando no terminal:

```bash
python manage.py makemigrations
```

Esse comando criará as migrações necessárias para criar as tabelas no banco de dados. Para executar as migrações, digite o seguinte comando no terminal:

```bash
python manage.py migrate
```

Por fim, vamos registrar a entidade `Produtora` no sistema de administração. Para isso, abra o arquivo `core/admin.py` e adicione o seguinte código:

```python
from django.contrib import admin

from .models import Categoria, Pais, TipoAtuacao, Produtora

...

admin.site.register(Produtora)
```

Com essas etapas realizadas, já é possível fazer o cadastro de produtoras no sistema de administração.

# Criando a entidade Membro

Agora vamos criar a entidade `Membro`. Abra o arquivo `core/models.py` e adicione o seguinte código:

```python
class Membro(models.Model):
    nome = models.CharField(max_length=100)
    pais = models.ForeignKey(Pais, on_delete=models.PROTECT)
    data_nascimento = models.DateField()

    def __str__(self):
        return self.nome
```

Esse é um exemplo similar ao anterior, mas adicionamos também um campo `data_nascimento`, que é uma instância de `models.DateField`. Esse campo representa uma data. O Django possui vários tipos de campos, que podem ser consultados na [documentação](https://docs.djangoproject.com/pt-br/4.2/ref/models/fields/).

Em seguida, faremos a migração e executaremos as migrações. Para isso, digite os seguintes comandos no terminal:

```bash
python manage.py makemigrations
python manage.py migrate
```

E, por fim, registramos a entidade `Membro` no sistema de administração. Para isso, abra o arquivo `core/admin.py` e adicione o seguinte código:

```python
from django.contrib import admin

from .models import Categoria, Pais, TipoAtuacao, Produtora, Membro

...

admin.site.register(Membro)
```

Com essas etapas realizadas, já é possível fazer o cadastro de membros no sistema de administração.

# Criando a entidade Filme

Agora vamos criar a entidade `Filme`. Abra o arquivo `core/models.py` e adicione o seguinte código:

```python
class Filme(models.Model):
    titulo = models.CharField(max_length=100)
    ano = models.IntegerField()
    classificacao = models.IntegerField()
    duracao = models.TimeField()
    sinopse = models.TextField()
    produtora = models.ForeignKey(Produtora, on_delete=models.PROTECT)

    def __str__(self):
        return self.titulo
```

Entre os campos da entidade `Filme`, temos um novo tipo que é `TimeField()` usado para representar um horário. 

Em seguida, vamos fazer as migrações e executá-las, com os seguintes comandos:

```bash
python manage.py makemigrations
python manage.py migrate
```

Por fim, vamos registrar a nova classe no sistema de administração. Para isso, abra o arquivo `core/admin.py` e adicione o seguinte código:

```python
from django.contrib import admin

from .models import Categoria, Pais, TipoAtuacao, Produtora, Membro, Filme

...

admin.site.register(Filme)
```

Com essas etapas realizadas, já é possível fazer o cadastro de filmes no sistema de administração.

É importante também sempre verificar as alterações no banco de dados SQLite, como visto anteriormente.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. "Início")</span>
<span> 
[As entidades associativas &gt;](entidades-associativas "Próximo")  </span></span>