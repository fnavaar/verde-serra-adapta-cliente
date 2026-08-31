# SPEC-1-002 — Acesso administrativo e segregação de papéis

**Fase:** 1 · **Status:** planejada · **Dono:** Administrador + executor Ethos  
**Origem:** RQ-006/RQ-007; AC-005 · **Degrau:** auth/RBAC nativos do Skip; nenhum novo IdP sem decisão.

## Contrato executável

**Resultado:** Administrador autenticado acessa `/admin`; Gestor só consulta superfícies liberadas; visitante e usuário sem papel não recebem dados administrativos. Acesso/negação relevante é rastreável sem segredo.

**Inclui:** login/logout autorizado, sessão, papéis Admin/Gestor, guarda de rota, negação por padrão e auditoria mínima.  
**Fora:** SSO, MFA, recuperação por e-mail, convite automático, papéis de hotel, automação de alçadas e dados reais.  
**Pré-condições:** ID do projeto, RBAC nativo comprovado, matriz Admin/Gestor aprovada e contas de teste. Se o recurso não atender, parar; não escolher biblioteca/IdP alternativo.

| Regra | Condição | Resultado |
|---|---|---|
| RN-001 | sem sessão válida | negar `/admin` e redirecionar ao login |
| RN-002 | Administrador ativo | permitir superfície F1 liberada |
| RN-003 | Gestor | somente leitura expressamente aprovada |
| RN-004 | acesso negado/papel alterado | evento com ator técnico, ação, horário e resultado; sem senha/token |

**Risco/reversão:** configuração permissiva exige prova negativa; indisponibilidade de auth mantém admin indisponível. Revogar papel/sessão e restaurar matriz documentada, sem apagar auditoria.

## Critérios de aceite
- [ ] **CA-1-101:** visitante não acessa nem recebe dados de `/admin`.
- [ ] **CA-1-102:** Administrador ativo acessa a superfície F1.
- [ ] **CA-1-103:** Gestor não executa ação não liberada.
- [ ] **CA-1-104:** logout/expiração retiram acesso; negações são rastreáveis sem segredo.

## TDD da SPEC

| Etapa | Prova | Evidência |
|---|---|---|
| RED | visitante abre `/admin`; Gestor tenta escrita | acesso/dados negados |
| GREEN | Administrador abre admin e cria dado permitido | rota/ação permitidas |
| REFACTOR/REGRESSÃO | logout, expiração e login de Gestor | sem persistência/elev. indevida |

**Fixtures:** Admin, Gestor e visitante; dados sintéticos.  
**Parar:** matriz/contas ausentes, recurso nativo insuficiente ou pedido de novo provedor.  
**Handoff:** demonstrar janela anônima, Gestor, Admin e logout.

## Tasks vinculadas

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|
| F1-T02 | Confirmar Skip e RBAC nativo | Executor Ethos | SPEC-1-002 | pré-condição | RED | registro/captura | acesso e matriz | Bloqueada |
| F1-T06 | Configurar guarda/negação | Executor Ethos | SPEC-1-002 | CA-1-101..104 | RED/GREEN | logs/capturas | F1-T02 aceita | Bloqueada |
| F1-T11 | Regressão e roteiro de aceite do acesso | Executor Ethos + Administrador | SPEC-1-002 | CA-1-101..104 | REGRESSÃO | logs, capturas, roteiro | F1-T06 aceita | Bloqueada |

## Emendas
| Data | Origem | Micro-spec/task | Motivo |
|---|---|---|---|
