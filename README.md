# API Testing Project - Open Library

Projeto pratico de **Testes de API** utilizando Postman, Newman e GitHub Actions.

## Sobre o Projeto

Este repositorio contem uma suite de testes automatizados para a API publica [Open Library](https://openlibrary.org), cobrindo:

- Happy Path (fluxos positivos)
- Edge Cases (casos de borda)
- Negative Tests (testes negativos)

## API Testada

**Open Library** - https://openlibrary.org

Catalogo aberto de livros mantido pela Internet Archive. Nao exige autenticacao.

| Endpoint | O que retorna |
|----------|---------------|
| /search.json?q= | Busca livros por titulo |
| /isbn/{isbn}.json | Dados de um livro por ISBN |
| /search/authors.json?q= | Busca autores por nome |
| /authors/{key}.json | Detalhes de um autor |
| /authors/{key}/works.json | Obras de um autor |
| /subjects/{assunto}.json | Livros por assunto |
| covers.openlibrary.org/b/isbn/{isbn}-M.jpg | Capa do livro |

## Estrutura do Repositorio

```
api-testing-project/
+-- README.md
+-- collections/
|   +-- OpenLibrary_API_Tests.postman_collection.json
+-- environments/
|   +-- openlibrary.postman_environment.json
+-- newman-reports/
+-- docs/
|   +-- APRESENTACAO.md
+-- .github/
    +-- workflows/
        +-- api-tests.yml
```

## Como Executar

### Pre-requisitos

- Node.js (v18+)
- Newman instalado globalmente

### Instalacao

```bash
npm install -g newman newman-reporter-htmlextra
```

### Executar testes via CLI

```bash
newman run collections/OpenLibrary_API_Tests.postman_collection.json -e environments/openlibrary.postman_environment.json -r htmlextra --reporter-htmlextra-export newman-reports/relatorio.html
```

## Metricas

| Categoria | Cenarios | Status |
|-----------|----------|--------|
| Happy Path | 7 | OK |
| Edge Cases | 4 | OK |
| Negative Tests | 5 | OK |
| **Total** | **16** | OK |

- **Validacoes automaticas:** 37
- **Taxa de sucesso:** 100%
- **Tempo de execucao:** ~17 segundos

## Tecnologias

- **Postman** - Criacao e execucao de testes
- **Newman** - Execucao via CLI
- **Newman HTMLExtra** - Relatorios visuais
- **GitHub Actions** - CI/CD automatizado
- **Open Library API** - API publica de livros

## Autor

Cristiane Sousa Alves - Estudo pratico de API Testing

## Licenca

MIT
