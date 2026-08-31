# Análise Crítica do Escopo — Concierge de Reservas 24h (v2 — 27/08/2026)

**Data:** 2026-08-27  
**Plano:** `Plano — 89c2ebd7` — Circuito Elegante / Verde Serra Central Hoteleira Ltda  
**Escopo analisado:** `03-Projeto/01-Escopo.md` (v2 — consolidada reunião de discovery de 27/08)  
**Rota / cadeia:** `skill-mind → gerar-escopo → idear-direcoes → definir-requisitos → revisar-escopo → analise-critica` · variante **profunda** · execução `fallback_serial`  
**Revisores:** revisor-de-plano, revisor-adversarial, revisor-viabilidade, guardião-de-escopo, explorador-de-alternativas  
**Runtime:** Ethos legado; contratos e scripts de ledger ausentes no workspace local.  
**Fontes verificadas:** DMO 18/08; Sales Call 12/08; Kickoff 20/08; **Discovery 27/08 (Navaar + Manoela + Mônica)**; atas, fluxos e insights no Drive. O vídeo de mapeamento prometido no kickoff não estava disponível; a discovery 27/08 trouxe detalhamento verbal do processo atual e da proposta.

## Veredito curto

A reunião de discovery de 27/08 **fechou decisões estruturais importantes** que reduzem a incerteza da 1ª entrega: site reconstruído no Skip, automação até o **pré-bloqueio via Omni**, pagamento/checkout no hotel (modelo Booking), área restrita com dashboard por hotel, notificação e-mail+WhatsApp ao concierge, formulário opcional de contexto sem IA, comissão direta como exceção e CRM de personalização adiado.

O escopo **continua sem estar pronto para implementação**, mas por uma razão mais específica que antes: falta a **prova técnica e contratual da Omni para o pré-bloqueio** (reunião OmniBiz de 28/08), o baseline de "imediato" e o mapa operacional completo de exceções. A direção é executável em ondas — e a discovery já definiu a fronteira que faltava.

## Matriz de rastreabilidade

| Fonte | Direção | Requisito | Achado / decisão |
|---|---|---|---|
| DMO 18/08: concierge 24h, motor de reservas, objetivo de eficiência | D1 prova Omni; D2 fluxo assistido | RQ-001, RQ-002, RQ-003 | AC-001, AC-002, DH-01 |
| Sales Call 12/08: tentativa anterior falhou; licença Omni citada | D1 prova de dados; D7 transparência | RQ-002, RQ-003, RQ-005 | AC-001, AC-004 |
| Kickoff 20/08: unidades habitacionais; até 48h → imediato | D4 site/D5 dashboard; D7 notificação | RQ-003, RQ-006 | AC-002, AC-003, DH-02 |
| **Discovery 27/08: site no Skip; automação até pré-bloqueio; pagamento no hotel; dashboard; notificação concierge; formulário opcional; comissão exceção; CRM adiado** | D3 pré-bloqueio; D4–D6; D7–D8 | RQ-001..RQ-008 | AC-004, AC-005, AC-006, DH-01..DH-06 |
| Sales Call: CRM com preferências de hóspedes | D9 adiar personalização | RQ-007 | AC-005, DH-04 |
| Discovery: concierge diferencia, precisa de dono/SLA de exceção | D7 notificação | RQ-004, RQ-008 | AC-006, DH-05 |
| Discovery: relatórios mensais por hotel; comissão como exceção | D8 relatórios; D10 exceção | RQ-006 | AC-007, DH-06 |

## Achados críticos

### AC-001 — A integração com Omni/OmniBiz (incluindo pré-bloqueio) é uma hipótese, não uma capacidade comprovada

- **Origem:** revisor-viabilidade, revisor-adversarial, revisor-de-plano.
- **Evidência:** a Sales Call (12/08) relata tentativa anterior de integração que operou por ~1,5 ano com erro de preço/disponibilidade e pouquíssimas vendas; a **discovery 27/08 decidiu automatizar até o pré-bloqueio via Omni**, mas o consultor afirmou que a Omni **não tem documentação pública de API** e que ele pesquisava em fóruns; reunião OmniBiz marcada para 28/08.
- **Cenário de falha:** o site aplica pré-bloqueio que a Omni não suporta de fato (ou bloqueia estoque sem autorização), repetindo o fracasso anterior e quebrando a confiança premium.
- **Decisão / ação:** condicionar **qualquer** automação de pré-bloqueio à prova técnica/contratual (docs, sandbox, credenciais, read/write, rate limits, hotéis cobertos, tempo de resposta). Enquanto não houver prova, manter pesquisa assistida + handoff (modelo "pré-bloqueio manual") como fallback.

### AC-002 — "Atendimento imediato" continua sendo uma intenção válida, mas não é uma métrica de aceite

- **Origem:** revisor-de-plano, revisor-adversarial.
- **Evidência:** kickoff (20/08) fixa a passagem de até 48h ou mais para "imediato"; DMO deixa métricas do time sem resposta; a discovery 27/08 reafirma o desejo de resposta rápida, mas não define SLA/percentil/canal/janela.
- **Cenário de falha:** sucesso declarado com resposta automática genérica enquanto consultas críticas seguem em fila; sem baseline não há antes/depois comparável nem atribuição de receita.
- **Decisão / ação:** definir antes da SPEC o evento inicial/final, canais incluídos, SLA/percentil de "imediato", janela de baseline e métricas de qualidade (erro, handoff, conversão atribuível).

### AC-003 — O mapa operacional que define regras, exceções e dados da consulta ainda não está completo

- **Origem:** revisor-de-plano, revisor-viabilidade.
- **Evidência:** kickoff exige vídeo detalhado; `03-fluxos_encontrados.md` do kickoff registra que o processo não foi desenhado; a discovery 27/08 detalhou o fluxo atual (pré-bloqueio com cartão, pagamento no hotel, casos de não comparecimento) e a proposta, mas não cobre todos os canais, campos, exceções, alteração/cancelamento e regras por hotel.
- **Cenário de falha:** a equipe técnica inventa campos, políticas e escalonamento.
- **Decisão / ação:** consolidar o mapa as-is/ASA completo (entrada, fontes, regras, exceções, saída, responsáveis, dados sensíveis) antes de SPEC.

### AC-004 — A primeira entrega tem fronteira definida (pré-bloqueio), mas a exceção de comissão direta precisa de regra explícita

- **Origem:** explorador-de-alternativas, revisor-viabilidade, guardião-de-escopo.
- **Evidência:** discovery 27/08 acorda automação **até o pré-bloqueio**, pagamento/checkout **no hotel** (modelo Booking); porém a cliente menciona casos de "receber direto do cliente e já descontar comissão", que o consultor classificou como exceção específica. Não há regra de **quando** aplicar, quem autoriza e como registrar.
- **Cenário de falha:** a exceção vira fluxo padrão em produção sem controle, gerando divergência de faturamento e de atribuição.
- **Decisão / ação:** definir explicitamente a exceção de comissão direta (autorizador, condição, registro) ou proibi-la na 1ª entrega.

### AC-005 — Notificação e-mail/WhatsApp com dados do hóspede e dashboard exigem base legal e minimização

- **Origem:** revisor-adversarial, revisor-viabilidade, guardião-de-escopo.
- **Evidência:** discovery 27/08 quer disparo automático de dados do hóspede (nome, telefone, hotel, datas) ao concierge e dashboard; existe CRM com preferências pessoais (pantufa, vinho, revista) que fica **fora** da 1ª entrega, mas o apetite de uso posterior permanece.
- **Cenário de falha:** dados pessoais são espalhados por e-mail/WhatsApp/dashboard sem consentimento, acesso por papel e retenção.
- **Decisão / ação:** excluir CRM de preferências da 1ª entrega (já decidido); definir base legal, minimização, acesso por papel, retenção e responsável antes de qualquer disparo automático.

### AC-006 — Sem dono e SLA de exceção, automação apenas desloca a demora

- **Origem:** revisor-de-plano, revisor-viabilidade.
- **Evidência:** discovery 27/08 reforça o concierge como diferencial e prevê contato pós-reserva, mas não define owner, cobertura, SLA nem alçadas de exceção (indisponibilidade, erro, alteração, pedido especial).
- **Cenário de falha:** casos críticos caem numa fila sem responsável e o hóspede continua esperando.
- **Decisão / ação:** nomear owner, cobertura, SLA e procedimento de handoff; testar a fila com cenários simulados.

### AC-007 — O escopo cresceu (site + dashboard + relatórios + notificação + formulário + integração); risco de fragmentação de ciclo

- **Origem:** guardião-de-escopo, explorador-de-alternativas.
- **Evidência:** discovery 27/08 agregou reestruturação do site no Skip, área restrita, dashboard por hotel, relatórios mensais, notificação concierge, formulário opcional e (adiado) CRM. Kickoff restringia a um processo.
- **Cenário de falha:** quatro meses se repartem entre site, gestão e integração e não provam o gargalo de resposta.
- **Decisão / ação:** ordenar por fase 1 com valor visível no gargalo (prova Omni + fluxo assistido); manter CRM, relatórios avançados e opcionais como evolução, não compromisso inicial.

## Decisões humanas

| ID | Decisão | Opções | Recomendação não vinculante | Decisor |
|---|---|---|---|---|
| DH-01 | Qual promessa cabe na primeira versão? | A consulta confiável + pré-bloqueio via Omni (conforme 27/08); B reserva transacional end-to-end no site | A, com o pré-bloqueio **condicionado à prova** da Omni; manter fallback manual | Consultor + champion + operação |
| DH-02 | Como medir "imediato"? | SLA simples; percentil por canal; resposta automática vs. resolução | Definir eventos, baseline, percentil e qualidade da resposta | Champion + consultor |
| DH-03 | Qual fonte e permissão de inventário/tarifa (e pré-bloqueio) são válidas? | Omni/OmniBiz licenciada; outra fonte autorizada; nenhum acesso ainda | Não iniciar automação de pré-bloqueio sem evidência documental e teste (28/08) | Cliente + Rubens/Omni + consultor |
| DH-04 | Dados de CRM entram na primeira onda? | Não; somente dados mínimos; personalização completa | Não; adiar até governança de dados aprovada | Cliente / jurídico / operação |
| DH-05 | Quem recebe exceções e com qual SLA? | Concierge; Mônica/equipe; escala híbrida | Nomear owner e backup antes do piloto | Champion + operação |
| DH-06 | Comissão direta do cliente entra como fluxo padrão? | Exceção específica (27/08); padrão automatizado; não entra | Exceção específica com regra de autorização/registro | Consultor + champion |

## Conselho de decisão — Sequência da primeira onda (pós-discovery 27/08)

**Arquiteto:** a discovery deu a fronteira (pré-bloqueio), mas o gate real segue sendo a prova da Omni. Sem prova de write/tempo de resposta, construir "pré-bloqueio automático" é assumir capacidade.

**Cético:** automatizar o pré-bloqueio muda a natureza da promessa: de consulta para reserva garantida. A pergunta é se o Circuito tem direito e inventário para isso — e se o hóspede entende que o pagamento ainda é no hotel.

**Pragmático:** site no Skip + captura estruturada + dashboard + notificação entrega valor visível enquanto a Omni é provada; o pré-bloqueio pode entrar como fase seguinte com evidência.

**Crítico:** notificar o concierge com dados do hóspede via e-mail/WhatsApp exige consentimento e acesso por papel antes do go-live. A exceção de comissão direta precisa de regra para não virar fluxo padrão.

### Veredito do conselho
- **Consenso:** manter a fronteira 27/08 (pré-bloqueio condicionado à prova; pagamento no hotel) e validar a Omni antes de automação comercial.
- **Dissenso mais forte:** site completo + dashboard pode atrasar a prova do gargalo se a fase 1 não priorizar o caminho crítico de resposta.
- **Checagem de premissa:** a reunião OmniBiz (28/08) precisa responder se pré-bloqueio é suportado por API, com que tempo e com que cobertura de hotéis.
- **Recomendação:** prova Omni + mapa operacional → site no Skip com captura estruturada, dashboard e handoff assistido → pré-bloqueio automático (condicionado) → decisão de transação end-to-end. A decisão final é humana.

## Aprendizados consultados

Não consultado — não havia caminho de segundo cérebro/configuração operacional disponível neste runtime. **Disposição:** `not-reusable`; as lacunas identificadas são específicas do onboarding, da licença e da operação deste caso, sem causa-raiz transversal comprovada.

## O que está sólido

- A discovery 27/08 fechou decisões estruturais: site no Skip, fronteira no pré-bloqueio, pagamento no hotel (modelo Booking), dashboard por hotel, notificação ao concierge, formulário opcional sem IA, comissão como exceção, CRM adiado.
- Processo prioritário (reservas de unidades habitacionais) e dor observável (retorno de até 48h ou mais, evasão para OTAs) reafirmados.
- Há data e dono para a prova da Omni (reunião OmniBiz 28/08) e call de implementação (31/08).

## Riscos residuais

- Prova da Omni para **pré-bloqueio** (write, tempo de resposta, cobertura de hotéis, política comercial).
- Baseline de "imediato" e definição de atribuição de ganho.
- Migração de dados/volume do site atual no Skip.
- Pagamento, confirmação, alteração, cancelamento, reembolso e suporte pós-reserva (ainda no hotel).
- Consentimento LGPD e acesso por papel para notificações e dashboard.
- Coerência cadastral: DMO usa "Verde Serra Central Hoteleira Ltda", enquanto reuniões citam "Circuito Elegante"; confirmar razão social/operação antes de integração.

## Próximo passo e gate

1. Consultor preenche `analise-do-consultor.md` respondendo AC-001..AC-007 e DH-01..DH-06, sem que a IA escolha por ele.
2. Cliente/operação entrega **prova OmniBiz** (28/08, 11h) com documentação, capacidade de pré-bloqueio e tempo de resposta; entrega mapa operacional completo e baseline.
3. Call de implementação (31/08, 10:45–12:00) fecha escopo exato de dashboard e formulário; com autoria humana e decisões registradas, executar `skill-mind job=escopo-definitivo`.

**Gate explícito:** não gerar SPEC, task nem implementar enquanto AC-001, AC-002, AC-003 e DH-01..DH-06 não tiverem respostas verificáveis; o pré-bloqueio automático só entra após prova técnica da OmniBiz.