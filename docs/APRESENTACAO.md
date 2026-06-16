# Apresentacao - Testes de API com Open Library

## Objetivo do Estudo

Desenvolver competencia pratica em **Testes de API** automatizados, utilizando ferramentas gratuitas, com foco em:
- Validacao automatica de respostas
- Geracao de relatorios visuais
- Automacao via CI/CD

---

## API Testada

| Item | Detalhe |
|------|---------|
| **API** | Open Library |
| **URL** | https://openlibrary.org |
| **O que faz** | Catalogo aberto de livros, autores e capas |
| **Autenticacao** | Nenhuma (API publica e gratuita) |
| **Mantida por** | Internet Archive |

---

## O que foi Testado

### Cenarios Cobertos

| Categoria | Quantidade | Exemplos |
|-----------|-----------|----------|
| Happy Path | 7 | Buscar livro por titulo, por ISBN, buscar autor, obras do autor, capa do livro, buscar por assunto |
| Edge Cases | 4 | Titulo muito longo, caracteres especiais, limit=1, ordenar por recente |
| Negative Tests | 5 | ISBN inexistente (404), autor inexistente, endpoint invalido, busca vazia |
| **Total** | **16** | |

### Endpoints Testados

| Metodo | Endpoint | O que retorna |
|--------|----------|---------------|
| GET | /search.json?q= | Busca livros por titulo |
| GET | /isbn/{isbn}.json | Dados de um livro por ISBN |
| GET | /search/authors.json?q= | Busca autores por nome |
| GET | /authors/{key}.json | Detalhes de um autor |
| GET | /authors/{key}/works.json | Obras de um autor |
| GET | /subjects/{assunto}.json | Livros por assunto |
| GET | covers.openlibrary.org/b/isbn/{isbn}-M.jpg | Capa do livro (imagem) |

---

## Metricas de Resultado

| Metrica | Valor |
|---------|-------|
| Total de requests | 16 |
| Total de validacoes (assertions) | 37 |
| Taxa de sucesso | **100%** |
| Tempo de execucao (Postman) | 13 segundos |
| Tempo de execucao (Newman) | 17 segundos |
| Tempo medio de resposta | 606 ms |
| Falhas | 0 |

---

## Ferramentas Utilizadas

| Ferramenta | Funcao | Custo |
|------------|--------|-------|
| Postman | Criar e rodar testes visualmente | Gratuito |
| Newman | Rodar testes pelo terminal + relatorios | Gratuito |
| Newman HTMLExtra | Relatorios visuais em HTML | Gratuito |
| GitHub | Hospedar e versionar o projeto | Gratuito |
| GitHub Actions | CI/CD automatico (roda testes a cada push) | Gratuito |

---

## Demonstracao Pratica

### Fluxo Executado

```
1. Buscar livro por titulo ("Lord of the Rings")
   -> Validar: status 200, lista com titulo e autor

2. Buscar livro por ISBN (9780140328721)
   -> Validar: status 200, titulo retornado

3. Buscar autor por nome ("J.K. Rowling")
   -> Validar: status 200, nome correto

4. Detalhes do autor
   -> Validar: nome, data de nascimento

5. Obras do autor
   -> Validar: lista de livros com titulo

6. Capa do livro por ISBN
   -> Validar: Content-Type = image, tamanho > 1KB

7. Buscar por assunto ("Science Fiction")
   -> Validar: nome do assunto, lista de obras

8. ISBN inexistente -> Validar: 404
9. Autor inexistente -> Validar: 404
10. Busca vazia -> Validar: API nao quebra (200)
```

---

## Beneficios para o Time

| Beneficio | Descricao |
|-----------|-----------|
| Deteccao precoce | Testes rodam a cada push, encontrando problemas antes |
| Documentacao viva | A colecao serve como especificacao da API |
| Regressao automatica | Elimina testes manuais repetitivos |
| Confianca em deploys | Pipeline barra codigo que quebra a API |
| Onboarding | Novos membros entendem a API pelos testes |

---

## Proximos Passos

| Acao | Prazo | Prioridade |
|------|-------|------------|
| Aplicar em APIs internas do time | 2 semanas | Alta |
| Workshop para o time (30 min) | 1 mes | Alta |
| Adicionar testes de contrato (schema) | 3 semanas | Media |
| Integrar relatorios com Jira | 1 mes | Media |
| Explorar testes de performance | 2 meses | Baixa |

---

## Links

- **Repositorio**: [github.com/cristianesousaalves/api-testing-project](https://github.com/cristianesousaalves/api-testing-project)
- **API testada**: [openlibrary.org](https://openlibrary.org)
- **Relatorio Newman**: Disponivel nos artifacts do GitHub Actions

---

## Conclusao

O estudo demonstrou que e possivel implementar testes de API automatizados com ferramentas **100% gratuitas**, em poucas horas, cobrindo cenarios positivos, de borda e negativos, com relatorios visuais e pipeline de CI/CD integrado.

A proposta e expandir essa pratica para as APIs do nosso produto, comecando pelos endpoints mais criticos.
