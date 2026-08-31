# SPEC-1-004 — Baseline e métrica de automatização

**Resultado:** contrato versionado com fonte, evento, hotel, período, numerador, denominador, fórmula, deduplicação, owner e limites — ou bloqueio explícito.

**Fórmula:** taxa = reservas concluídas por fluxo automatizado/Omni comprovado ÷ reservas concluídas elegíveis da mesma fonte/hotel/período × 100. D=0 é não aplicável; ausência de fonte/evento/meta é bloqueio, não estimativa.

**Fora:** dashboard, Omni real, meta automática, go-live e atribuição financeira. **Pré-condição:** fonte/definição/autorizações aprovadas.

**Aceite:** cálculo reproduzível ou bloqueio válido com owner/próxima revisão. **TDD:** RED fonte ausente/D=0/duplicidade; GREEN 6 de 10 = 60%; regressão com versionamento.

**Tasks:** F1-T03, F1-T09, F1-T13.