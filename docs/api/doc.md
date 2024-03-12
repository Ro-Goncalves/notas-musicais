# Documentação

``` mermaid
flowchart
    doc --> InicioRapido
    doc --> Resumo
    doc --> Tutorial
    doc --> ComoContribuir
    
    Tutorial --> Instalacao
    InicioRapido --> Instalacao

    Resumo --> Cards

    ComoContribuir --> API
    ComoContribuir --> ComoExecutar

    ComoExecutar --> Clone
    ComoExecutar --> Testes
    ComoExecutar --> Linter
```

## Resumo

### Cards

- Cards para levar para lugares específicos da documentação.  
  - Inicio Rápido
  - Tutorial
  - Contribuição

### Inicio Rápido

- Contexto sobre a aplicação
  - subcomandos
- Como Instalar
  - pip install ...
- Como Executar
  - Gancho com o contexto e uma explicação básica de cada comando
  - Help!

## Tutorial

- Detalhar os objetivos
- Explicar cada subcomando
  - Variações dos comandos
  - Aproveitar dos recursos gráficos
    - Imagens e vídeos
  - Problemas comuns?

## Quero contribuir

- Como executar o projeto
  - Como fazer o clone
  - Como rodar os testes
  - Como rodar os linters
  - Descrições do módulos
    - Aponta para a documentação da API.
- Dicas de contribuição - com referências - dizer onde está
  - Implementar escalas
    - Wiki das escalas
  - Classes customizadas de Erros
    - NotaErro
  - Progressões harmônicas
    - Implementação de tríades
      - sus4
      - sus9
    - Tétrade
      - Acordes com 7
      - Acorder com 9
  - Funções harmônicas
    - Tônica
    - dominante
    - subdominante
    - Relativos

## API

- Explicar os módulos!

---

## Parte Técnica

- Macros: Não repita comando que podem se modificar
- Templates: para que blocos de codumentação repitida não sejam duplicados em vários lugares.
- Cards: CSS e HTML
