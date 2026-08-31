# Índice de SPECs — Fase 1 — Circuito Elegante / Verde Serra

**Gerado em:** 2026-08-28  
**Envelope:** `SKILLMIND_ENVELOPE v1` · `run_id: manual-fallback-20260828-verde-serra-f1` · `requested_job: gerar-specs` · `authorized_skill: gerar-specs` · `stage_index: 1` · `runtime_profile: ethos-legacy`  
**Estado:** planejadas; nenhuma task foi gerada ou autorizada.

| SPEC | Resultado observável | Requisitos/origem | Dependência crítica | Status |
|---|---|---|---|---|
| SPEC-1-001 | Catálogo público navegável em preview | RQ-001; AC-003; VC-010 | inventário/conteúdo e projeto Skip autorizados | planejada |
| SPEC-1-002 | Área admin protegida por papel | RQ-006, RQ-007; AC-005 | matriz e mecanismo nativo de auth/RBAC | planejada |
| SPEC-1-003 | Cadastro e consulta auditável de hotéis/reservas administrativas | RQ-005..008; AC-004..006 | SPEC-1-002 + persistência nativa identificada | planejada |
| SPEC-1-004 | Contrato e baseline (ou bloqueio) da taxa de automatização | RQ-003; AC-002; VC-006 | fonte/evento/fórmula/meta aprovados | planejada |

## Revisão serial do painel

- **Analista de SPECs:** aprovado com bloqueios explícitos de inventário, matriz de acesso, persistência nativa e definição da métrica; cada lacuna impede a task correspondente, não será improvisada.
- **Revisor de SPECs:** aprovado; 4 SPECs cobrem resultado público, permissão, dados e métrica — faixa 3–7; todas têm degrau, fronteira, aceite binário, TDD e tasks vazias.
- **Revisor de risco e segurança:** aprovado com condições: negação por padrão, nenhum segredo/dado real em fixtures, auditabilidade mínima, sem chamada Omni/Resend, sem pagamento; falha de auditoria bloqueia escrita.
- **Revisor de TDD:** aprovado; RED/GREEN/regressão ligados aos critérios, com alternativas de teste nativo ou roteiro quando o projeto ainda não estiver acessível. Antes de gerar tasks, o executor deverá substituir “comando nativo do projeto” pelo comando real detectado no repositório autorizado.

## Próxima etapa segura

Executar `gerar-tasks` somente após validação humana destas SPECs. A execução posterior seleciona uma única task elegível, roda provas e aguarda teste humano antes de avançar.
