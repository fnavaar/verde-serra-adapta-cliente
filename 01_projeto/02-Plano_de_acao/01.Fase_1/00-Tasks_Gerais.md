# Tasks Gerais — Fase 1 — Circuito Elegante / Verde Serra

**Estado:** planejada; uma task por vez, com prova e teste humano antes do avanço.  
**Gates:** `check-escopo.md` APROVADO_COM_RESSALVAS; `check-cliente.md` APROVADO.

## Tasks

| ID | Onda | Task | Dono | SPEC | Critério | Prova | Evidência | Pré-condição | Parar quando | Status |
|---|---:|---|---|---|---|---|---|---|---|---|
| F1-T01 | 1 | Consolidar inventário | Administrador | SPEC-1-001 | inventário completo/aprovado | RED | inventário | fontes de conteúdo | insumo incompleto | Elegível |
| F1-T02 | 1 | Confirmar Skip/RBAC | Executor Ethos | SPEC-1-002 | projeto/RBAC ou bloqueio formal | RED | registro técnico | acesso Skip/matriz | RBAC insuficiente | Bloqueada |
| F1-T03 | 1 | Aprovar baseline | Gestor/champion | SPEC-1-004 | fonte, evento, período, fórmula, deduplicação/meta ou bloqueio | RED | contrato/bloqueio | fonte autorizada | definição ausente | Bloqueada |
| F1-T04 | 2 | Implementar catálogo | Executor Ethos | SPEC-1-001 | CA-1-001/002/004 | GREEN/REGRESSÃO | preview/testes | F1-T01 aceita | rota/conteúdo fora do escopo | Bloqueada |
| F1-T05 | 2 | Testar CTA sem Omni | Executor Ethos | SPEC-1-001 | CA-1-003 | RN-002/REGRESSÃO | rede/captura | F1-T04 aceita | chamada Omni/coleta | Bloqueada |
| F1-T06 | 2 | Configurar acesso | Executor Ethos | SPEC-1-002 | CA-1-101..104 | RED/GREEN | logs/capturas | F1-T02 aceita | política não confirmada | Bloqueada |
| F1-T07 | 3 | Implementar modelo | Executor Ethos | SPEC-1-003 | CA-1-201/202/204 | RED/GREEN | esquema/testes | F1-T06 aceita | dado pessoal/campo novo | Bloqueada |
| F1-T08 | 3 | Implementar flag/trilha | Executor Ethos | SPEC-1-003 | CA-1-203/205 | GREEN/REGRESSÃO | evento/teste | F1-T07 aceita | cálculo/auditoria falha | Bloqueada |
| F1-T09 | 3 | Registrar baseline/bloqueio | Administrador | SPEC-1-004 | CA-1-301..304 | GREEN/REGRESSÃO | contrato/cálculo | F1-T03 aceita | D=0/duplicidade/fonte incompleta | Bloqueada |
| F1-T10 | 4 | Regressão catálogo | Executor Ethos | SPEC-1-001 | CA-1-001..004 | REGRESSÃO | logs/preview/roteiro | F1-T05 aceita | CA sem prova | Bloqueada |
| F1-T11 | 4 | Regressão acesso | Executor Ethos | SPEC-1-002 | CA-1-101..104 | REGRESSÃO | logs/roteiro | F1-T06 aceita | CA sem prova | Bloqueada |
| F1-T12 | 4 | Regressão registros | Executor Ethos | SPEC-1-003 | CA-1-201..205 | REGRESSÃO | logs/roteiro | F1-T08 aceita | CA sem prova | Bloqueada |
| F1-T13 | 4 | Regressão baseline | Administrador | SPEC-1-004 | CA-1-301..304 ou bloqueio válido | REGRESSÃO | contrato/roteiro | F1-T09 aceita | CA sem prova | Bloqueada |

## Regras de execução

- `Elegível` não autoriza implementação: o consultor autoriza explicitamente uma única task.
- Ao concluir, rodar prova, registrar evidência e aguardar teste humano explícito.
- F1-T10..F1-T13 são regressões independentes, cada uma vinculada a uma única SPEC; falha retorna à SPEC de origem.
