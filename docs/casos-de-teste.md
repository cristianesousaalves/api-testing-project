# Casos de Teste - Open Library API

## 01 - Happy Path (Cenarios Positivos)

| # | Caso de Teste | Endpoint | Resultado Esperado |
|---|---------------|----------|-------------------|
| 1 | Buscar livro por titulo | GET /search.json?q=lord+of+the+rings | Status 200, lista com titulo e autor |
| 2 | Buscar livro por ISBN | GET /isbn/9780140328721.json | Status 200, dados do livro |
| 3 | Buscar autor por nome | GET /search/authors.json?q=j.k.+rowling | Status 200, autor encontrado |
| 4 | Detalhes do autor | GET /authors/OL23919A.json | Status 200, nome e data de nascimento |
| 5 | Obras de um autor | GET /authors/OL23919A/works.json | Status 200, lista de obras |
| 6 | Capa do livro por ISBN | GET covers.openlibrary.org/b/isbn/978...-M.jpg | Status 200, Content-Type: image |
| 7 | Buscar por assunto | GET /subjects/science_fiction.json | Status 200, nome do assunto e obras |

## 02 - Edge Cases (Casos de Borda)

| # | Caso de Teste | Endpoint | Resultado Esperado |
|---|---------------|----------|-------------------|
| 8 | Titulo muito longo | GET /search.json?q=(texto longo) | Status 200, numFound presente |
| 9 | Caracteres especiais | GET /search.json?q=cafe | Status 200, aceita sem erro |
| 10 | Limit = 1 resultado | GET /search.json?q=harry+potter&limit=1 | Status 200, exatamente 1 resultado |
| 11 | Ordenar por recente | GET /search.json?q=python&sort=new | Status 200, resultados retornados |

## 03 - Negative Tests (Cenarios Negativos)

| # | Caso de Teste | Endpoint | Resultado Esperado |
|---|---------------|----------|-------------------|
| 12 | ISBN inexistente | GET /isbn/0000000000000.json | Status 404 |
| 13 | Autor inexistente | GET /authors/OL99999999A.json | Status 404 |
| 14 | Endpoint invalido | GET /api/naoexiste.json | Status 404 ou 400 |
| 15 | Busca vazia | GET /search.json?q= | Status 200, API nao quebra |
| 16 | Capa ISBN inexistente | GET covers.openlibrary.org/b/isbn/000...-M.jpg | Retorna resposta (placeholder) |

---

## Resumo

- **Total de casos:** 16
- **Validacoes (assertions):** 37
- **Taxa de sucesso:** 100%
