# SPEC-1-001 — Catálogo público e migração de conteúdo

**Fase:** 1 · **Status:** planejada · **Dono:** Administrador + executor Ethos  
**Origem:** RQ-001; AC-003/DH-01; VC-010 · **Degrau:** recursos nativos do Skip; sem CMS, Omni ou motor de inventário.

## Contrato executável

**Resultado:** em preview, visitante percorre inicial → catálogo → detalhe de hotel e vê apenas conteúdo aprovado. O CTA “Consultar reserva” informa que a integração será futura; não consulta Omni, não cria reserva, não coleta dados nem solicita pagamento.

**Inclui:** rotas públicas, catálogo/detalhe, importação do conteúdo aprovado, catálogo vazio, hotel inexistente e metadados básicos.  
**Fora:** disponibilidade, reserva/pré-bloqueio, preço, pagamento, formulário, e-mail, rastreamento e administração.  
**Pré-condições:** inventário aprovado contendo origem/destino, título/texto, mídia/direito, status e aprovador por item; acesso ao projeto Skip. Sem insumo, parar — jamais copiar, fabricar ou publicar conteúdo.

| Regra | Condição | Resultado |
|---|---|---|
| RN-001 | hotel aprovado, completo e não arquivado | exibir no catálogo/detalhe |
| RN-002 | CTA acionado | informar indisponibilidade da integração; zero chamadas externas |
| RN-003 | slug inválido | estado “hotel não encontrado”, sem dados de outro hotel |

**Risco/reversão:** mídia sem direito ou conteúdo desatualizado não migra; inventário vazio gera estado vazio, não dados fictícios. Reverter preview/retirar item preservando o inventário.

## Critérios de aceite
- [ ] **CA-1-001:** visitante abre catálogo e detalhe de cada hotel aprovado.
- [ ] **CA-1-002:** item incompleto, não aprovado ou arquivado não é público.
- [ ] **CA-1-003:** CTA não chama Omni, não cria reserva e não solicita pagamento.
- [ ] **CA-1-004:** catálogo vazio e rota inexistente são claros e não expõem dados indevidos.

## TDD da SPEC

| Etapa | Prova | Evidência |
|---|---|---|
| RED | item incompleto e slug inexistente | item não publica; 404/estado correto |
| GREEN | dois hotéis sintéticos aprovados | catálogo/detalhes corretos e CTA inerte |
| REFACTOR/REGRESSÃO | catálogo vazio, arquivado e CTA | sem regressão de navegação ou fronteira Omni |

**Fixtures:** dois hotéis sintéticos aprovados, um incompleto e um arquivado; nenhum dado de hóspede.  
**Parar:** falta de inventário, direito de mídia, autorização Skip ou decisão de conteúdo/CTA.  
**Handoff:** demonstrar catálogo, detalhe, rota inválida, vazio e CTA no preview.

## Tasks vinculadas

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|
| F1-T01 | Consolidar e aprovar inventário | Administrador | SPEC-1-001 | inventário completo/aprovado | RED | inventário | fontes de conteúdo | Elegível |
| F1-T04 | Implementar catálogo e estados | Executor Ethos | SPEC-1-001 | CA-1-001/002/004 | GREEN | preview/testes | F1-T01 aceita | Bloqueada |
| F1-T05 | Verificar CTA sem Omni | Executor Ethos | SPEC-1-001 | CA-1-003 | REGRESSÃO | rede/captura | F1-T04 aceita | Bloqueada |
| F1-T10 | Regressão e roteiro de aceite do catálogo | Executor Ethos + Administrador | SPEC-1-001 | CA-1-001..004 | REGRESSÃO | logs, preview, capturas, roteiro | F1-T05 aceita | Bloqueada |

## Emendas
| Data | Origem | Micro-spec/task | Motivo |
|---|---|---|---|
