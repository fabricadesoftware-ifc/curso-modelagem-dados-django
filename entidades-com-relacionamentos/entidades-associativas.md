---
title: "Entidades associativas"
permalink: /entidades-com-relacionamentos/entidades-associativas
---

# Entidades associativas

Uma entidade associativa é uma entidade que representa um relacionamento entre outras entidades. Por exemplo, considere o relacionamento entre as entidades `Filme` e `Categoria`. Um filme pode pertencer a várias categorias, e uma categoria pode ter vários filmes. Para representar esse relacionamento, podemos criar uma entidade associativa `FilmeCategoria`, que representa a associação entre um filme e uma categoria. Essa entidade possui um relacionamento com as entidades `Filme` e `Categoria`, além de um terceiro atributo, que representa a data de associação entre o filme e a categoria. 

Um segundo exemplo é um tripla associação entre `Filme`, `Membro` e `TipoAtuacao`. Um filme pode ter vários membros do elenco, e um membro de elenco pode participar de vários filmes. Para representar esse relacionamento, podemos criar uma entidade associativa `Atuacao`, que representa a atuação de um membro de elenco em um filme. Essa entidade possui um relacionamento com as entidades `Filme` e `Membro`, além de um terceiro atributo, que representa o tipo de atuação do membro no filme.

## Criando a entidade FilmeCategoria

Para representar a associação entre `Filme` e `Categoria` usaremos um tipo de relacionamento chamado *ManyToManyField*. Abra o arquivo `core/models.py` e editar a criação da classe `Filme`, adicionando o seguinte atributo:

```python
class Filme(models.Model):
    ...
    categorias = models.ManyToManyField(Categoria)
```

Note que manteremos todos os atributos da classe `Filme` que já havíamos criado anteriormente. O novo atributo `categorias` é uma instância de `models.ManyToManyField`, que representa um relacionamento *ManyToMany* com a entidade `Categoria`.

Após adicionar esse atributo, é necessário fazer as migrações e executá-las, como já fizemos em outros casos. Para isso, executamos os seguintes comandos:

```bash
python manage.py makemigrations
python manage.py migrate
```

Nesse caso, as migrações do Django irão adicionar uma nova entidade ao banco dados, que pode ser visualizada no SQLite. Note que a nova entidade, chamada `core_filme_categoria`.

Também, É possível perceber que no sistema de administração um novo tipo de campo foi adicionado possibilitando associar várias categorias a um único filme.

## A associação de Filmes, Membros e TipoAtuacao

Já a associação entre `filme`, `membro` e `tipoAtuacao`, faremos usando uma classe para representá-la. Para isso, editaremos o arquivo `core/models.py` e adicionaremos os seguintes comandos:

```python
class Atuacao(models.Model):
    filme = models.ForeignKey(Filme, on_delete=models.PROTECT)
    membro = models.ForeignKey(Membro, on_delete=models.PROTECT)
    tipo_atuacao = models.ForeignKey(TipoAtuacao, on_delete=models.PROTECT)
    personagem = models.CharField(max_length=100, blank=True, null=True)
```

Nesse exemplo, criamos uma entidade que possui três chaves estrangeiras, formando o conceito de uma entidade associativa. Além disso, adicionamos um atributo `personagem` não obrigatório.

Em seguida, devemos fazer a migração para integrar as novas alterações no banco de dados:

```bash
python manage.py makemigrations
python manage.py migrate
```

Por fim, vamos registrar a nova classe no sistema de administração. Para isso, editaremos o arquivo `core/admin.py` e adicionamos:

```python
...
from .models import Categoria, Pais, TipoAtuacao, Produtora, Atuacao

...

admin.site.register(Atuacao)
```

# Conclusão da aula

Com essas implementações temos as principais representações de entidades e seus relacionamentos no Django.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Entidades com chaves estrangeiras](entidades-com-chaves-estrangeiras "Anterior")</span>
<span> 
[Sumário &gt;](../ "Início")  </span></span>

