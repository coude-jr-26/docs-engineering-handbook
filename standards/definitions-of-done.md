# Definição de Pronto

Uma tarefa só pode ser considerada pronta quando todos os critérios necessários forem atendidos.

A definição de pronto evita entregas incompletas, reduz retrabalho e ajuda o time a manter qualidade mesmo com várias pessoas trabalhando ao mesmo tempo.

## Critérios gerais

A tarefa está pronta quando:

- [ ] O que foi pedido na task foi implementado.
- [ ] Os critérios de aceite foram atendidos.
- [ ] O código foi testado localmente.
- [ ] Não há erros conhecidos introduzidos pela alteração.
- [ ] A branch está atualizada com a branch base.
- [ ] O Pull Request foi aberto com descrição clara.
- [ ] O Pull Request foi revisado e aprovado.
- [ ] Todos os comentários da revisão foram respondidos.
- [ ] A documentação foi atualizada quando necessário.

## Código

- [ ] A funcionalidade foi implementada conforme especificado.
- [ ] O código segue o padrão do projeto.
- [ ] Não há código comentado sem justificativa.
- [ ] Não há `TODO` sem número de issue associado.
- [ ] Não há `console.log`, `dd()`, `dump()`, `var_dump()` ou código de debug.
- [ ] Não há senhas, tokens, chaves de API ou dados sensíveis no código.
- [ ] Arquivos `.env` não foram enviados para o repositório.
- [ ] O arquivo `.env.example` foi atualizado quando houve nova variável de ambiente.

## Backend

Para tarefas no `crm-backend`:

- [ ] Controllers estão simples e delegam regras de negócio para services, actions ou classes apropriadas.
- [ ] Validações de entrada estão em Form Requests quando aplicável.
- [ ] Respostas da API usam códigos HTTP corretos.
- [ ] Erros esperados são tratados.
- [ ] Migrations foram criadas quando houve alteração de banco.
- [ ] Seeders foram atualizados quando necessário.
- [ ] Models, relationships e casts foram configurados corretamente.
- [ ] Não há queries inseguras ou SQL manual desnecessário.
- [ ] Endpoints protegidos exigem autenticação quando necessário.

## Frontend

Para tarefas no `crm-frontend`:

- [ ] Componentes estão organizados e com responsabilidade clara.
- [ ] Tipos TypeScript foram definidos corretamente.
- [ ] Não há uso de `any` sem justificativa.
- [ ] Estados de loading foram tratados.
- [ ] Estados de erro foram tratados.
- [ ] Formulários têm validação adequada.
- [ ] Chamadas à API usam a configuração centralizada.
- [ ] Dados sensíveis não são salvos de forma insegura.
- [ ] A interface foi testada no navegador.

## Infraestrutura

Para tarefas no `crm-infra`:

- [ ] O Docker Compose está válido.
- [ ] Os containers sobem sem erro.
- [ ] Serviços essenciais estão configurados.
- [ ] PostgreSQL está acessível.
- [ ] Redis está acessível.
- [ ] Nginx está configurado quando aplicável.
- [ ] Volumes foram definidos corretamente.
- [ ] Networks foram definidas corretamente.
- [ ] O README explica como executar o ambiente.
- [ ] Comandos de instalação foram testados localmente.

## Qualidade

Para tarefas do time de QA:

- [ ] Cenários de teste foram documentados.
- [ ] Fluxos principais foram testados manualmente.
- [ ] Fluxos de erro foram testados manualmente.
- [ ] Bugs encontrados foram registrados com evidência.
- [ ] Casos de regressão foram considerados.
- [ ] Quando aplicável, testes automatizados foram criados ou atualizados.

## Testes

- [ ] Testes unitários foram criados para nova lógica quando aplicável.
- [ ] Testes existentes continuam passando.
- [ ] Testes de integração foram criados quando necessário.
- [ ] O fluxo principal foi validado manualmente.
- [ ] Se houver pipeline de CI configurado, todos os checks devem passar.

Comandos comuns:

```bash
# Backend
docker compose exec app php artisan test

# Frontend
docker compose exec frontend npm test
docker compose exec frontend npm run lint

# Infraestrutura
docker compose config
docker compose up -d
```

## Revisão

- [ ] O Pull Request foi revisado por pelo menos uma pessoa.
- [ ] Mudanças críticas foram revisadas por um Tech Lead.
- [ ] Comentários de revisão foram respondidos.
- [ ] Sugestões aceitas foram aplicadas.
- [ ] Sugestões recusadas foram justificadas tecnicamente.
- [ ] O autor não fez merge do próprio Pull Request sem autorização.

## Documentação

- [ ] README foi atualizado se o modo de executar mudou.
- [ ] Documentação de API foi atualizada se endpoints mudaram.
- [ ] Documentação de ambiente foi atualizada se variáveis mudaram.
- [ ] Decisões técnicas relevantes foram registradas.
- [ ] Lógica complexa tem comentários explicando o motivo da decisão.

## Segurança

- [ ] Nenhum segredo foi enviado para o repositório.
- [ ] Dados sensíveis não aparecem em logs.
- [ ] Endpoints privados exigem autenticação.
- [ ] Permissões foram respeitadas.
- [ ] Validações impedem entrada inválida.
- [ ] Não há exposição desnecessária de dados do usuário.

## Entrega

A entrega está completa quando:

- [ ] O Pull Request foi aprovado.
- [ ] O merge foi feito na branch correta.
- [ ] A branch da feature foi removida após o merge.
- [ ] O status da task foi atualizado no Jira.
- [ ] O time foi informado sobre a conclusão quando necessário.

## Observação sobre staging

Quando o ambiente de staging estiver disponível, tarefas que alterem comportamento do sistema devem ser verificadas em staging antes de serem consideradas finalizadas.

Enquanto staging não estiver disponível, a validação local com Docker é obrigatória.
