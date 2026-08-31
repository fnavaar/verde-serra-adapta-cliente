# Escopo Definitivo — Circuito Elegante / Verde Serra

**Versão:** 1.1 · **Data:** 28/08/2026
**Plano:** `Plano — 89c2ebd7`
**Fontes consolidadas:** `01-Escopo.md` v2 (27/08), `analise-critica.md` v2, `analise-do-consultor.md` com checkpoint autorizado, `requisitos.md` e `revisao-do-escopo.md`.
**Revisão documental (28/08):** painel adversarial (A1–A9) e coerência (VC-001..VC-011); correções `safe_auto` aplicadas, lacunas `gated_auto`/`manual` registradas em "A confirmar".

## 1. Resultado de negócio

Entregar uma plataforma de descoberta e reserva de hotéis do Circuito Elegante que use o Omni como fonte operacional de disponibilidade e reserva, reduza a dependência de atendimento manual para garantir uma vaga e preserve o concierge como responsável pela confirmação e pelo handover de amenities.

A experiência deve permitir que o hóspede pesquise e inicie/efetive a reserva por uma interface própria, inspirada na clareza de uma OTA, sem deslocar checkout ou pagamento para a plataforma. A operação terá área restrita para administração de reservas diretas/por indicação, marcação da exceção de comissão e leitura de ocupação e reservas por hotel.

**Métrica norte:** proporção de reservas concluídas pelo fluxo automatizado/Omni, medida por hotel e por período. A linha de base, fórmula final, meta e fonte serão fechadas na Fase 1; não se declara "atendimento imediato" sem essa medição.

> **Mudança de métrica (decisão do consultor, AC-002/DH-02):** a métrica norte passa a ser a **taxa de automatização da reserva** (reservas concluídas pelo fluxo automatizado/Omni), substituindo o objetivo de "tempo de retorno" do escopo base. O tempo de resposta permanece como objetivo de experiência, sem meta declarada até baseline. Não declarar conversão/atribuição sem fonte e evento de reserva definidos na Fase 1.

## 2. Atores e fluxo-alvo

- **Hóspede:** pesquisa hotéis/unidades, informa o recorte necessário e conclui a reserva no fluxo autorizado pelo Omni; recebe confirmação pelo canal definido pelo hotel/Omni.
- **Concierge da operação (Circuito Elegante):** recebe e-mail operacional após a reserva, contata o hóspede quando necessário e conduz confirmação/handover de amenities/suporte.
- **Hotel:** confirma a chegada e conduz check-in/pagamento (fora da automação); a Omni restringe-se a reserva/bloqueio conforme capacidade comprovada.
- **Administrador da plataforma:** administra hotéis, registros de reserva/indicação, exceções de comissão e acompanha relatórios.
- **Gestor:** consulta indicadores de reserva e ocupação por hotel e os relatórios necessários à operação.

**Fluxo ASA:** descoberta no site → consulta/ação de reserva no Omni → registro de evento → e-mail ao concierge → confirmação de chegada/pagamento no hotel e suporte/amenities pelo concierge (procedimento a fechar na call 31/08) → registro de exceção quando reserva for direta/indicação → leitura de operação por hotel.

## 3. Capacidades incluídas e fronteiras

### Incluído
- Site reconstruído no Skip, com catálogo/apresentação dos hotéis e experiência de pesquisa/reserva; migração/transporte do conteúdo atual definido na Fase 1 (inventário de páginas na call 31/08).
- Integração com Omni para as capacidades de disponibilidade, reserva e bloqueio/pré-bloqueio que forem efetivamente disponibilizadas à operação (prova técnica/contratual antes de SPEC).
- E-mail transacional via Resend ao concierge após evento de reserva, com dados mínimos necessários (consentimento/rol de campos e provider validados antes do envio real).
- Área restrita administrativa: hotéis, reservas diretas/por indicação, sinalização de comissão direta e relatórios de ocupação/reservas por hotel.
- Formulário opcional de contexto no fechamento da reserva (Fase 2), sem IA generativa; uso operacional pela área restrita na Fase 3.
- Controles de acesso por papel, trilha dos eventos relevantes, minimização de dados e procedimento para falhas/exceções.

### Fora de escopo deste ciclo
- Checkout, pagamento, reembolso ou conciliação financeira na plataforma; pertencem ao hotel (no check-in). A Omni restringe-se a reserva/bloqueio conforme capacidade comprovada.
- Cancelamento, alteração, no-show e conciliação de cobrança entre Circuito Elegante e hotéis: pertencem ao hotel/Omni; o sistema registra o evento, não resolve a transação financeira.
- CRM de personalização de hóspedes, preferências e campanhas de relacionamento.
- WhatsApp como canal automatizado de notificação interna; o concierge pode usá-lo no seu contato com o hóspede fora da automação.
- IA para atendimento, recomendação ou interpretação de formulário.
- Automação de políticas comerciais que não estejam confirmadas pela operação/Omni.
- Reuso/personalização futura dos dados do formulário opcional sem nova decisão de governança.

## 4. Decisões consolidadas e limites ainda verificáveis

| Decisão do consultor | Reflexo no escopo |
|---|---|
| O Omni já executa agendamento e bloqueio/reserva (AC-001/DH-03). | A plataforma se integra ao Omni e não recria motor de inventário ou pagamento; cada operação só se implementa após prova em ambiente/contrato autorizado. |
| Reserva pelo Omni; concierge finaliza relação e amenities (AC-002/DH-02). | E-mail operacional é handoff, não substituição da operação do hotel; confirmação de chegada/pagamento no hotel, suporte/amenities pelo concierge. |
| Métrica de automatização é a norte (AC-002/DH-02). | Medição por hotel e período; baseline/fórmula/meta/fonte fechados na Fase 1. Tempo de resposta permanece como objetivo de experiência. |
| Resend é o canal de disparo (AC-005). | Notificação automatizada fica limitada a e-mail nesta entrega; provider validado (Resend ou equivalente) antes do envio real. |
| Área administrativa concentra indicação/contato direto, comissão e relatórios (AC-004/DH-04). | CRM administrativo é operacional e limitado; não é CRM de personalização. |
| Comissão direta é rara e registrada como exceção (AC-004/DH-06). | O administrador a marca no registro da reserva; não se cria fluxo de comissão no site público. Regra de comissão (quando aplicar, quem autoriza, como registrar) definida antes do primeiro relatório mensal. |

**A confirmar antes da SPEC que a depender disso (lacunas gated_auto/manual):**
1. **Omni/OmniBiz (gate 28/08 11h):** contrato, credenciais, sandbox, endpoints e capacidade real de reserva/pré-bloqueio/cancelamento; comportamento em falha; cobertura de hotéis; política de revenda. Nenhuma SPEC poderá inventar esses itens.
2. **E-mail ao concierge (F2):** consentimento explícito do hóspede (ou base legal equivalente validada) + rol de campos aprovado por papel antes do envio real; provider de e-mail validado (Resend ou equivalente); teste de falha.
3. **Fronteira de transações (F2):** cancelamento/alteração/no-show/reembolso e conciliação de cobrança pertencem ao hotel/Omni; o sistema registra o evento, não resolve a transação.
4. **Comissão direta (F3):** regra de comissão (quando aplicar, quem autoriza, como registrar) definida pela operação antes da emissão do primeiro relatório mensal; origem "indicação/contato direto" precisa de política de rastreabilidade para não virar via paralela de faturamento.
5. **Dados/formulário opcional (global):** finalidade limitada ao atendimento/operação; reuso/personalização futura exige nova decisão de governança; retenção/base legal a aprovar.
6. **Loops (F4):** cada loop declara fonte, baseline, alvo, unidade, cadência, veredito e responsável; conectores (Omni, Resend/SMTP, Skip Cloud) são hipóteses até validação na call de setup; métrica norte fechada na F1 (fonte + evento de "reserva concluída").
7. **Identidade jurídica (manual):** Verde Serra Central Hoteleira Ltda × marca Circuito Elegante — confirmar razão social/CNPJ do piloto antes de SPEC da F2.
8. **Confirmação/cancelamento por hotel, papéis e acessos (call 31/08):** responsáveis da área restrita, alçadas, owner/SLA de exceções (inclui comissão direta) e procedimento de confirmação/handover.
9. **Baseline e métrica (F1):** linha de base, fórmula final, meta e fonte da taxa de automatização; sem baseline não há atribuição; tempo de resposta não é critério de sucesso comercial — conversão/atribuição o é.

## 5. Plano de execução — cinco fases

### Fase 1 — Fundação pública e operação administrativa visível
**Resultado:** hóspede navega por um site próprio e a operação dispõe de área restrita inicial para cadastrar/consultar hotéis e reservas administrativas.

**Capacidades:** site no Skip; catálogo e páginas de hotel; migração/transporte do conteúdo atual (inventário de páginas na call 31/08); autenticação e perfis administrativos; modelo mínimo de hotéis, reservas, origem (site/indicação/contato direto) e marcação de comissão direta; registro de eventos; captura de baseline e definição da métrica norte (fonte + evento de "reserva concluída" fechados aqui).

**Fora da fase:** ação de reserva integrada ao Omni, e-mail automatizado, relatórios consolidados e CRM de personalização.

**Aceite:** ambiente acessível; administrador autorizado cria e consulta registros; visitante percorre descoberta de hotel; dados e permissões passam casos de teste definidos; baseline, fórmula, meta e fonte de automação registrados ou bloqueio explicitamente documentado; fonte e definição de evento da métrica norte registrados como critério de aceite explícito.

**Gate:** validação humana do fluxo público e administrativo antes das SPECs da Fase 2.

### Fase 2 — Reserva integrada ao Omni e handoff ao concierge
**Resultado:** o hóspede executa o fluxo de pesquisa/reserva autorizado pelo Omni e o concierge recebe o handoff por e-mail.

**Capacidades:** integração Omni com credenciais autorizadas; consulta/ação apenas nas operações comprovadas; exibição de origem/validade quando fornecidas; fallback seguro em falha; e-mail Resend com mínimo necessário (consentimento + rol de campos aprovados); formulário opcional de contexto no fechamento da reserva (sem IA); estados e trilha de reserva; tratamento de erro, indisponibilidade e duplicidade.

**Fora da fase:** checkout/pagamento próprio, promessa de bloqueio sem prova da API, WhatsApp automatizado, cancelamento/alteração/no-show/reembolso e conciliação de cobrança (pertencem ao hotel/Omni; o sistema registra o evento, não resolve a transação financeira).

**Aceite:** testes contra sandbox/ambiente autorizado provam o percurso combinado; falha Omni não gera confirmação inventada; e-mail chega ao destinatário de teste com dados minimizados e consentimento registrado; reserva/evento é rastreável; roteiro humano é aprovado.

**Gate:** prova técnica e contratual das capacidades Omni usadas; confirmação humana do fluxo de ponta a ponta.

### Fase 3 — Controle operacional e visão por hotel
**Resultado:** administração acompanha reservas e ocupação por hotel, trata reservas diretas/indicação e registra comissão como exceção.

**Capacidades:** dashboard e relatórios por hotel a partir de fontes disponíveis; filtros e recortes autorizados; fila/registro de exceções; campos de owner, estado e prazo conforme política operacional definida; uso operacional do formulário de contexto coletado na F2; exportação somente se aprovada.

**Fora da fase:** personalização de hóspedes, campanhas de CRM e decisões automáticas sobre comissão.

**Aceite:** dados de teste chegam ao recorte correto; perfil sem permissão não acessa outro hotel; uma reserva direta e uma exceção de comissão são registradas e auditáveis (com regra de comissão definida antes do primeiro relatório mensal); relatório é conciliável com a fonte definida.

**Gate:** operação valida dados, papéis e procedimento de exceção.

### Fase 4 — Loops e agentes de operação
**Resultado:** os sistemas das Fases 1–3 passam a ser acompanhados em ciclos mensuráveis, sem delegar decisões comerciais ou de privacidade a agentes.

- **Loop de confiabilidade de reserva:** mede eventos com falha/fallback, pendências e recuperação. Fonte: logs/trilha da plataforma e Omni. Métrica, baseline e alvo a confirmar na call de setup.
- **Loop de conversão automatizada:** mede a proporção de reservas pelo fluxo Omni por hotel. Fonte: eventos de reserva validados (definição fechada na F1). Veredito: gestor/champion, não o agente.
- **Loop de saúde operacional:** acompanha exceções de indicação/comissão e registros sem desfecho. Fonte: área administrativa. O loop alerta e prepara relatório; a decisão é humana.

**Aceite:** cada loop tem fonte acessível, métrica, responsável, cadência, limite de autonomia e procedimento de recuperação documentados; conectores e permissões são validados antes de ativação; baseline/alvo/veredito declarados por loop.

### Fase 5 — Validação integral e decisão de encerramento/go-live
**Resultado:** comprovar que o conjunto opera com segurança e valor no fluxo real, ou registrar pendências sem mascará-las.

**Matriz de validação:** regressão do site/admin (F1); consulta/reserva Omni, handoff, consentimento e fallbacks (F2); dashboard, exceção e segregação de acesso (F3); métricas, cadência e recuperação dos loops (F4); privacidade, duplicidade, timeout, cancelamento/alteração conforme capacidade Omni e rollback.

**Aceite:** roteiro executado pelo champion; evidências por requisito e fase; comparação com baseline quando disponível; riscos residuais e decisão humana de go-live/encerramento registrados. Item sem prova fica pendente.

## 6. Riscos e gates globais

1. **Integração Omni:** só se implementa cada operação após prova em ambiente/contrato autorizado. Fallback mantém o hóspede informado e encaminha para o procedimento humano definido.
2. **Dados pessoais:** e-mail contém apenas campos necessários; acesso é por papel; retenção, base legal e responsáveis precisam ser aprovados antes de dados reais; finalidade limitada ao atendimento/operação; reuso para personalização exige nova decisão de governança.
3. **Qualidade de inventário/reserva:** fonte, timestamp e validade são preservados quando disponíveis; não se informa disponibilidade como fato após falha.
4. **Exceções:** reserva direta/indicação e comissão exigem owner, procedimento e prazo definidos pela operação antes da automação operacional correspondente; regra de rastreabilidade definida para não virar via paralela de faturamento.
5. **Escopo:** CRM de personalização, pagamento e IA permanecem fora deste ciclo; qualquer expansão passa por decisão registrada.
6. **Métrica:** "tempo de resposta não é critério de sucesso comercial; conversão/atribuição o é". Sem baseline não há atribuição.

## 7. Matriz resumida de rastreabilidade

| Fonte/achado | Decisão | Requisito | Fase |
|---|---|---|---|
| AC-001 / DH-03 | Omni é motor operacional; integrar capacidades comprovadas | RQ-002, RQ-005 | 2 |
| AC-002 / DH-02 | Métrica é automatização de reserva; concierge confirma/handover | RQ-003, RQ-004 | 1, 2, 4, 5 |
| AC-003 / DH-01 | Reestruturar site e preparar/usar integração sem inventar regras | RQ-001, RQ-008 | 1, 2 |
| AC-004 / DH-06 | Comissão direta é exceção administrativa | RQ-005, RQ-008 | 3 |
| AC-005 / DH-04 | Admin operacional; dados minimizados | RQ-006, RQ-007 | 1, 3, 5 |
| AC-005 / decisão Resend | Handoff por e-mail ao concierge | RQ-004, RQ-007 | 2 |
| AC-006 / DH-05 | Exceções registradas na área restrita | RQ-008 | 3, 4, 5 |
| AC-007 | Entregas verticais e CRM de personalização adiado | RQ-001..008 | 1–5 |
| VC-001 | Ator "Concierge da operação (Circuito Elegante)"; hotel no check-in | RQ-004 | 1, 2, 3 |
| VC-002 | Pagamento/checkout no hotel (não na Omni); Omni só reserva/bloqueio | RQ-002 | global |
| VC-003 | Formulário de contexto no fechamento da reserva (F2); uso na F3 | RQ-008 | 2, 3 |
| VC-004 | Confirmação de chegada no hotel; suporte/amenities pelo concierge | RQ-004 | 2 |
| VC-006 | Métrica norte = taxa de automatização (substitui tempo de resposta) | RQ-003 | 1, 4, 5 |
| VC-010 | Migração de conteúdo atual na F1 | RQ-001 | 1 |
| A1 | Cancelamento/alteração/no-show/reembolso fora da plataforma | RQ-005 | 2 |
| A2 | Consentimento + rol de campos + teste de falha do e-mail | RQ-004, RQ-007 | 2 |
| A3/A5/A9 | Fronteiras de comissão, dados e métrica | RQ-005, RQ-007, RQ-008 | 3, 4, 5 |
| A4/A8 | Loops com baseline/alvo/fonte; conectores como hipóteses | RQ-003, RQ-006 | 4 |
| A6 | Identidade jurídica Verde Serra × Circuito Elegante (manual) | — | antes F2 |
| A7 | Rastreabilidade de indicação/contato direto | RQ-005 | 3, 4 |

## 8. Próximo passo seguro

Registrar o **check interno de escopo como pendente** e colher aprovação de Consultor/CSM/cliente. Após esse gate e as respostas da reunião OmniBiz (28/08 11h), gerar SPECs profundas apenas da Fase 1; não gerar tasks nem iniciar implementação nesta consolidação.