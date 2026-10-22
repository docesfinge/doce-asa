# doce-asa

Documentação estudantil para a disciplina Administração de Sistemas Abertos (ASA).

Em um Codespace do GitHub, execute os seguintes comandos:

1. `curl -LsSf https://astral.sh/uv/install.sh | sh`
2. `uv --version`
3. `uv init`
4. `uv add sphinx myst-parser sphinx-autobuild `
5. `uv add furo sphinx_book_theme sphinx-rtd-theme`
6. `uv run sphinx-quickstart`
   1. Separate source and build directories (y/n) [n]: `yes`
   2. Project name: `doce-asa`
   3. Author name(s): `{Nome} {Sobrenome}`
   4. Project release []: `2026`
   5. Project language [en]: `pt_BR`

8. `mv source docs`
9. `sed -i s/source/docs/  Makefile `
10. `uv run make`
11. `uv run make html`
12. `uv run sphinx-autobuild docs build/html`
13. # => Clique na URL que é exibida, como <http://127.0.0.1:8000>.

## Execução, teste e personalização

1. Abra outro terminal e execute: `code ./docs/conf.py`
2. Altere a variável `html_theme` para `"furo"`, `"sphinx_book_theme"` ou `"sphinx_rtd_theme"`[^1]
3. Crie 3 arquivos de exemplo: `touch  docs/{pedra,papel,tesoura}.md`
4. No arquivo `docs/conf.py`, adicione a extensão `"myst_parser"`[^2]
5. Adicione título `# Pedra`, `# Papel` e `# Tesoura` aos arquivos `docs/{pedra,papel,tesoura}.md`
6. Edite o arquivo `docs/index.rst`. Dentro da diretiva `toctree` , adicione referência aos arquivos `pedra.md`, `papel.md` e `tesoura.md`. A extensão `.md` é opcional. Exemplo:

   ```text
    .. toctree::
    :maxdepth: 2
    :caption: Sumário

    pedra
    papel
    tesoura

   ```

8.  Vá ao ChatGTP e faça consultas separadas sobre a história da pedra, do papel e da tesoura. Copie e cole a resposta nos respectivos arquivos: `pedra.md`, `papel.md` ou `tesoura.md`
9.  Pesquise no Google por [Myst Markdown Cheat Sheet](http://google.com/search?q=Myst+Markdown+Cheat+Sheet)
10. Insira a imagem de uma pedra no arquivo `pedra.md`
11. Insira a figura de uma pedra, com legenda, no arquivo `pedra.md`


## Vantagens do Sphinx com a extensão Myst/Markdown

1. A linguagem de marcação simplificada Markdown é simples que a linguage RestructuredText;
2. Arquivos externos podem literalmente ser inclusos em sua documentação.

## Exemplo de poder do Python Sphinx

Vamos simular a inclusão de um arquivo externo a um documento Markdown. Execute:

1. `mkdir ./docs/inc`
2. `cp pyproject.toml ./docs/inc`

No arquivo `pedra.md`, insira o seguinte código:

````
```{literalinclude} ./inc/pyproject.toml
```
````

Veja o resultado em seu navegador. Pesquise mais sobre a [diretiva literalinclude](https://www.sphinx-doc.org/pt-br/master/usage/restructuredtext/directives.html#directive-literalinclude).


Exemplo de arquivo incluso com numeração de linha:

````
```{literalinclude} ./inc/pyproject.toml
:linenos:
```
````

[^1]: Lembre-se das aspas duplas.
[^2]: Observe que, para o comando `uv add`, os pacotes podem ter menos(`-`) no nome. Já no arquivo de configuração `./docs/conf.py`, os pacotes serão referenciados pelo nome, com o menos(`-`) substituído por *underline* (`_`).
