# Testes de Login

## O que foi feito

Criação dos testes automatizados para o fluxo de login (`POST /api/login`), referente à task **SCRUM-25**, em `tests/Feature/LoginTest.php`.

Foram implementados 10 cenários de teste:

| # | Cenário | Status esperado |
|---|---|---|
| 1 | Login com credenciais válidas | 200 |
| 2 | Resposta de sucesso contém token | JSON com campo `token` |
| 3 | Login com senha incorreta | 401 |
| 4 | Login com email inexistente | 401 |
| 5 | Login com campos vazios (email e senha) | 422 |
| 6 | Login com email vazio (isolado) | 422 |
| 7 | Login com senha vazia (isolada) | 422 |
| 8 | Login com formato de email inválido | 422 |
| 9 | Login com email em maiúsculo | 200 (case insensitive) |
| 10 | Login com espaços em branco no email | 200 (normalização) |

## Como foi feito

1. Antes de escrever os testes, a rota foi validada manualmente via Postman (teste de mesa), pra confirmar o comportamento real da API.
2. Os testes automatizados (teste unitário) foram escritos seguindo **TDD (Test-Driven Development)**: o comportamento esperado foi definido em código antes da implementação da lógica de login estar pronta, servindo como contrato para as demais partes da Epic.

## Por que esses cenários

Além do caminho feliz e de um erro genérico, a cobertura inclui:

- **Validação de formato de email**, não só presença do campo
- **Isolamento de campos** (email e senha testados separadamente)
- **Normalização de dados** (case sensitivity e espaços em branco)
- **Verificação do conteúdo da resposta** (`assertJsonStructure`), não apenas do status HTTP

## Referências

- Pull Request: [#4](https://github.com/coude-jr-26/crm-backend/pull/4)
- Card Jira: [SCRUM-25](https://limalipe355.atlassian.net/browse/SCRUM-25)