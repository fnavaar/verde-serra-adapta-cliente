# SPEC-1-003 — Registros operacionais

**Resultado:** Admin cria/consulta hotéis e reservas sintéticas com origem `site`, `indicação` ou `contato_direto`; comissão é flag auditável; escrita deixa evento.

**Fora:** Omni, confirmação, cálculo/pagamento, dashboard, exportação e dado real. **Pré-condição:** acesso da SPEC-1-002, persistência nativa e campos aprovados. Falha de auditoria bloqueia escrita.

**Aceite:** vínculo e origem validados; duplicidade/autorização inválida não persistem; flag não calcula/paga; evento mínimo existe.

**TDD:** RED hotel ausente/origem inválida/duplicidade; GREEN indicação com flag; regressão de negação/auditoria.

**Tasks:** F1-T07, F1-T08, F1-T12.