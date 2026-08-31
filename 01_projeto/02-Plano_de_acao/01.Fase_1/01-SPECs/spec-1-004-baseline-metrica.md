# SPEC-1-004 — Baseline e métrica de automatização

**Fase:** 1 · **Status:** planejada · **Dono:** Gestor/champion + Administrador  
**Origem:** RQ-003; AC-002/DH-02; VC-006 · **Degrau:** contrato documental mínimo; não fabricar telemetria/conversão.

## Contrato executável

Contrato versionado informa fonte, evento de reserva concluída, hotel, período, referências, numerador, denominador, fórmula, deduplicação, validador e limitações — ou registra bloqueio explícito.

**Fórmula:** numerador = concluídas por fluxo automatizado/Omni comprovado; denominador = concluídas elegíveis da mesma fonte/hotel/período; taxa = `N/D × 100`. Cada ID entra uma vez. D=0 = `não aplicável`, nunca 0%. Fonte/evento/meta ausentes = `bloqueado`, nunca estimativa.  
**Fora:** dashboard, Omni real, meta automática, go-live, atribuição financeira e alteração de reservas. **Parar:** fonte/evento/período/fórmula/meta ausentes, dado pessoal sem autorização ou divergência de contagem.

## Critérios de aceite
- [ ] **CA-1-301:** contrato identifica fonte, evento, hotel, período, fórmula, deduplicação, owner e versão.
- [ ] **CA-1-302:** dados completos reproduzem a taxa.
- [ ] **CA-1-303:** insuficiência, duplicidade sem solução ou D=0 não geram taxa enganosa.
- [ ] **CA-1-304:** Gestor aprova definição/meta ou bloqueio com responsável/próxima revisão.

## TDD da SPEC
| Etapa | Prova | Evidência |
|---|---|---|
| RED | fonte ausente, D=0, ID duplicado | bloqueado/não aplicável, sem cálculo |
| GREEN | 10 concluídas, 6 automatizadas | 60,0% reproduzível |
| REFACTOR/REGRESSÃO | corrigir referência em versão nova | histórico preservado e nova versão rastreável |

**Fixtures:** contagens sintéticas; dados reais somente com acesso/finalidade aprovados. **Handoff:** contrato, fixture 60%, D=0 e bloqueio.

## Tasks vinculadas
| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|
| F1-T03 | Aprovar contrato e fonte de baseline | Gestor/champion | SPEC-1-004 | pré-condição | RED | contrato/bloqueio | fonte autorizada | Bloqueada |
| F1-T09 | Registrar baseline ou bloqueio | Administrador | SPEC-1-004 | CA-1-301..304 | GREEN/REGRESSÃO | contrato/cálculo | F1-T03 aceita | Bloqueada |
| F1-T13 | Regressão e roteiro de aceite do baseline | Administrador + Gestor | SPEC-1-004 | CA-1-301..304 | REGRESSÃO | contrato, cálculo/bloqueio, roteiro | F1-T09 aceita | Bloqueada |

## Emendas
| Data | Origem | Micro-spec/task | Motivo |
|---|---|---|---|
