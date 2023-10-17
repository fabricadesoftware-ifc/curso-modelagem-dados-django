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

<span style="display: flex; justify-content: space-between;"><span>[&lt; Início](. "Início")</span>
<span></span></span>