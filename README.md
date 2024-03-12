# Projeto Notas Músicais

## Configurando o ambiente

- **instalar o pipx** `pip install pipx`
- **instalar o poetry** `pipx install poetry`
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
- **ferramenta para criar macros na documentação** `poetry add --group doc mkdocs-macros-plugin`
- **ferramenta para colocar uma variável dentro do arquivo** `poetry add --group doc jinja2`

## Comandos Impostantes

- `poetry shell` : ativa o ambiente virtual
- `mkdocs serve` : sobe um servidor web com as documentações
- `blue --check --diff .` : verifica o code stily do projeto
- `isort --check --diff .` : checa se os imports estão organizados
- `task -l` : retorna as tasks configuradas no taskipy

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

watch:
  - notas_musicais # Toda vez que atualizar o arquivo, sobe a atualização

plugins:
  mkdocstrings:
    handlers:
      python:
        paths: [notas_musicais]
```

## Configurando Pytest

Essas configurações devem ser realizadas no arquivo pyproject.toml, de inicio é simples

```toml
[tool.pytest.ini_options]
pythonpath = "." #Caminho do projeto
addopts = "--doctest-modules" #Lê as docstrings
```

## Configurando linters

Estamos de bem com o **blue**, só precisamos fazer alguns poucos ajustes no **isort**

```toml
[tool.isort]
profile = "black" # Ajusta o padrão de identação, deixando igual a do blue
line_length =  79 # Quantidade máxima de caracteres por linha, deixando igual a do blue
```

## Configurando automações

Esse é um pouco chatinho, mas contém coisas bem legais.

```toml
[tool.poetry.scripts] # Para executar o CLI usando notas-musicais
notas-musicais = "notas_musicais.cli:app"

[tool.taskipy.tasks]
lint = "blue --check --diff . && isort --check --diff ." # permite usar task lint e executar o comando
docs = "mkdocs serve" # Gera a documentação
pre_test = "task lint" # Antes da task test executa o comando
test = "pytest -s -x --cov=notas_musicais -vv" # Task de teste 
                                               # s para permitir a saída de logs e prints durante a execução dos testes; 
                                               # -x para interromper a execução dos testes assim que um deles falhar; 
                                               # --cov=notas_musicais para gerar a cobertura de código da biblioteca;
                                               # -vv para exibir os resultados de cada teste de forma detalhada.
post_test = "coverage html" # Após a task test executa o comando
```
