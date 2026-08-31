# SPEC-1-002 — Acesso administrativo

**Resultado:** Administrador acessa `/admin`; Gestor só lê o que a matriz liberar; visitante e usuário sem papel não recebem dados.

**Inclui:** auth/RBAC nativo, sessão, Admin/Gestor, guarda de rota, negação por padrão e auditoria mínima. **Fora:** SSO, MFA, convites, dados reais. **Pré-condição:** projeto Skip, RBAC nativo comprovado, matriz e contas de teste. Sem isso, parar; não escolher IdP alternativo.

**Aceite:** visitante negado; Admin permitido; Gestor sem escrita; logout/expiração removem acesso e logs não contêm segredo.

**TDD:** RED visitante/Gestor; GREEN Admin; regressão logout/expiração.

**Tasks:** F1-T02, F1-T06, F1-T11.