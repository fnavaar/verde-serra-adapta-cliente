# Check de Escopo — Circuito Elegante / Verde Serra

**Estado:** APROVADO_COM_RESSALVAS  
**Data:** 2026-08-28  
**Escopo avaliado:** `03-Projeto/02-Escopo-Definitivo.md` v1.1 (ID `15LT7jkHdMaiSfXJ6fmlZq3DAqdTkalPT`).

## Controles internos verificados

- [x] Entrada: escopo base canônico, análise crítica e autoria humana com checkpoint autorizado existem.
- [x] Exatamente cinco fases: F1–F3 sistemas; F4 loops/agentes; F5 validação integral.
- [x] Entrega visível e critérios de aceite declarados por fase.
- [x] Fronteiras explícitas: pagamento/checkout no hotel (Omni só reserva/bloqueio conforme prova); CRM de personalização, IA e WhatsApp automatizado fora.
- [x] Rastreabilidade de AC/DH/RQ para decisão e fase registrada (inclui achados VC-001..VC-011 e A1..A9 do painel documental).
- [x] Riscos/gates Omni, dados pessoais, exceção operacional, baseline e métrica preservados.
- [x] Correções `safe_auto` aplicadas pelo agente principal (redação/reposicionamento, sem decisão nova); lacunas `gated_auto`/`manual` registradas em "A confirmar".
- [x] Consultor confirmou nesta sessão a aprovação dos gates para gerar as SPECs da Fase 1.

## Ressalvas e limites vigentes

- [x] A aprovação libera **somente as SPECs da Fase 1**; não autoriza tasks nem implementação.
- [x] Omni: contrato, credenciais e comportamento de operações continuam bloqueando qualquer SPEC/execução dependente da Fase 2.
- [x] Baseline, fórmula, meta, fonte e evento de reserva concluída continuam pré-condição da execução de `SPEC-1-004`; na ausência de fonte, o resultado correto é bloqueio explícito, não estimativa.
- [x] Matriz de papéis/alçadas e contas de teste são pré-condição de `SPEC-1-002`; não se presume RBAC/provedor alternativo.
- [x] Inventário/conteúdo aprovado é pré-condição de `SPEC-1-001`; não se fabrica conteúdo ou mídia.
- [x] Identidade jurídica, consentimento/rol de e-mail e confirmação/cancelamento por hotel permanecem gates da Fase 2.

> Este controle registra a autorização declarada pelo consultor para a geração das SPECs da Fase 1. Não substitui os gates humanos e técnicos reservados às fases seguintes.