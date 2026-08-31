# SPEC-1-003 — Registros operacionais

**Fase:** 1 · **Status:** planejada · **Dono:** Administrador + executor Ethos  
**Origem:** RQ-005..008; AC-004..006 · **Degrau:** persistência nativa autorizada; sem CRM, Omni ou regra financeira.

## Contrato executável

Admin cria e consulta hotéis e reservas **sintéticas**, seleciona `site`, `indicação` ou `contato_direto` e pode marcar comissão direta como exceção. Escrita aceita registra evento auditável. Não há confirmação/estado do Omni.

**Inclui:** modelo, formulários/lista/detalhe, validação, flag, filtro e auditoria. **Fora:** Omni, confirmação, cálculo/cobrança, dashboard, exportação e dados reais. **Parar:** persistência não identificada, pedido de dado pessoal/campo novo ou fronteira transacional alterada.

| Regra | Resultado |
|---|---|
| hotel/origem inválidos ou ID duplicado | rejeitar sem persistência parcial |
| comissão direta | flag auditável; sem cálculo/pagamento |
| escrita aceita | evento com entidade, ator técnico, horário e resultado |
| auditoria falha | bloquear escrita |

## Critérios de aceite
- [ ] **CA-1-201:** Admin cria/consulta hotel e reserva sintéticos.
- [ ] **CA-1-202:** vínculo de hotel e enum de origem são validados.
- [ ] **CA-1-203:** comissão é flag, sem automação financeira.
- [ ] **CA-1-204:** inválido/duplicado/sem autorização não persiste parcialmente.
- [ ] **CA-1-205:** escrita aceita deixa evento mínimo.

## TDD da SPEC
| Etapa | Prova | Evidência |
|---|---|---|
| RED | hotel ausente, origem inválida, ID repetido | rejeição sem persistência |
| GREEN | Admin cria hotel/indicação com flag | lista, detalhe e evento |
| REFACTOR/REGRESSÃO | escrita por Gestor/visitante; alteração válida | negação e auditoria preservada |

**Fixtures:** somente dados sintéticos. **Handoff:** criar hotel, registrar indicação, abrir histórico, testar origem inválida.

## Tasks vinculadas
| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|
| F1-T07 | Implementar modelo mínimo e validação | Executor Ethos | SPEC-1-003 | CA-1-201/202/204 | RED/GREEN | esquema, testes, capturas | F1-T06 aceita; persistência/campos aprovados | Bloqueada |
| F1-T08 | Implementar flag e trilha de eventos | Executor Ethos | SPEC-1-003 | CA-1-203/205 | GREEN/REGRESSÃO | detalhe, evento, teste | F1-T07 aceita | Bloqueada |
| F1-T12 | Regressão e roteiro de aceite dos registros | Executor Ethos + Administrador | SPEC-1-003 | CA-1-201..205 | REGRESSÃO | logs, capturas, roteiro | F1-T08 aceita | Bloqueada |

## Emendas
| Data | Origem | Micro-spec/task | Motivo |
|---|---|---|---|
