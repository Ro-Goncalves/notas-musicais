# Projeto Notas Músicais

## Configurando o ambiente

- **instalar o pipx** `pip install pipx`
- **instalr o poetry** `pipx install poetry`
- **criar novo projeto com poetry** `poetry new [nome-projeto]`
- **ferramenta que cria o gitignore** `pipx install ignr`
- **criar .gitignore de python** `ignr -p python > .gitignore`
- **ferramenta para test** `poetry add --group dev pytest`
- **ferramenta de cobertura** `poetry add --group dev pytest-cov`
- **ferramenta estilo do código** `poetry add --group dev blue`
- **ferramenta para ordenar imports** `poetry add --group dev isort`
- **ferramenta para documentar o código** `poetry add --group doc mkdocs-material`
- **ferramenta para criar doc string** `poetry add --group doc mkdocstrings`
- **ferramenta para criar doc string de python** `poetry add --group doc mkdocstrings-python`
- **ferramenta para automação de tarefas** `poetry add --group dev taskipy`

## Comandos Impostantes

- `poetry shell`: ativa o ambiente virtual
- `mkdocs serve`: sobe um servidor web com as documentações

## Configurando MKDOCS

Começamos com `mkdocs new .`, o ponto indica onde será criado a documentação, nesse caso, na pasta em que o comando foi executado, pode colocar em qualquer lugar.

No arquivo **mkdocs.yml**, devemos definir algumas configurações

```yml
site_name: Notas Musicais #Configura o nome do projeto
repo_url: https://github.com/Ro-Goncalves/notas-musicais # Link do repositório
repo_name: ro-goncalves/notas-musicais # Nome do repositório
edit_uri: tree/master/docs # Caminho da documentação

theme:  
  name: material # Configura o nome do tema  
  language: pt-BR # Configura o idioma
  logo: assets/logo.png # Configura o logo
  favicon: assets/logo.png # Configura o favicon

markdown_extensions:
  - attr_list # Permite colocar atributos no markdown, exemplo ![logo-projeto](assets/logo.png){width="300"}

extra_css:
  - stylesheets/extra.css # Inclui um CSS no doc
```
