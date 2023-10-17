---
title: "Entidades com relacionamentos"
description: Criação das entidades com relacionamentos
permalink: /entidades-com-relacionamentos/
---

# Entidades com relacionamentos

Nesta aula, vamos criar as entidades com relacionamentos. São elas:

* Produtora
* Membro
* Filme

Nessas três entidades, além dos atributos comuns, temos atributos que são referências para outras entidades. Esses atributos são chamados de chaves estrangeiras, e são usados para estabelecer relacionamentos entre as entidades.

Por exemplo, as entidades `membro` e `produtora` possuem um relacionamento com a entidade `pais`, de forma que cada membro e cada produtora deve ter um país de origem. Para isso, vamos criar um atributo `pais` nas entidades `membro` e `produtora`, que será uma referência para a entidade `pais`. Da mesma forma, a entidade `filme` possui um relacionamento com a entidade `produtora`, de forma que cada filme deve ter uma produtora. Para isso, vamos criar um atributo `produtora` na entidade `filme`, que será uma referência para a entidade `produtora`.

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. "Início")</span>
<span> 
[Criandos as entidades com chaves estrangeiras &gt;](entidades-com-chaves-estrangeiras "Próximo")  </span></span>