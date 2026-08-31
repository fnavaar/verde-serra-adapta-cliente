# Revisão do Escopo — Circuito Elegante (v2 — 27/08/2026)

**Cobertura:** DMO 18/08, Sales Call 12/08, Kickoff 20/08, **Discovery 27/08** (Navaar + Manoela + Mônica), escopo v2, direções v2, requisitos v2. **Método:** painel serial (revisor-de-plano, revisor-adversarial, revisor-viabilidade, guardião-de-escopo, explorador-de-alternativas) — `fallback_serial`.

## Achados

### RV-001 — Integração Omni (pesquisa + pré-bloqueio) segue sem evidência operacional; a discovery elevou a aposta para write
- **Gravidade/confiança:** grave / 100.
- **Evidência:** call comercial relata licença e tentativa anterior instável (preço/disponibilidade errados); discovery 27/08 **decidiu automatizar até o pré-bloqueio via Omni**; sem documentação pública de API (consultor pesquisa em fóruns) até a reunião OmniBiz 28/08.
- **Cenário de falha:** o site publica pré-bloqueio que a Omni não suporta de verdade (ou que bloqueia estoque sem autorização), repetindo o fracasso anterior e afetando a confiança premium.
- **Decisão necessária:** condicionar pré-bloqueio automático à **prova técnica/contratual**; manter pesquisa e handoff como fallback se a write não for confirmada.

### RV-002 — "Atendimento imediato" continua sem métrica operacional especificada
- **Gravidade/confiança:** grave / 100.
- **Evidência:** kickoff define redução de até 48h para imediato; DMO deixa métricas do time como "???"; discovery 27/08 reafirma querer "resposta rápida", mas não define SLA/percentil.
- **Cenário de falha:** sucesso declarado com resposta automática genérica, sem baseline comparável e sem atribuição de receita.
- **Decisão necessária:** definir evento inicial/final, percentil/SLA, canal, janela e baseline.

### RV-003 — O processo detalhado (vídeo/mapeamento) ainda não foi entregue; a discovery trouxe informações, mas não o mapa operacional completo
- **Gravidade/confiança:** grave / 100.
- **Evidência:** kickoff exige vídeo; a discovery 27/08 detalha o fluxo atual e a proposta (pré-bloqueio via Omni, pagamento no hotel, notificação concierge), mas não cobre todos os canais, campos, exceções, alterações/cancelamentos e regras de hotel.
- **Cenário de falha:** a construção inventa campos, políticas e exceções.
- **Decisão necessária:** consolidar o mapa as-is/ASA completo antes de SPEC.

### RV-004 — A fronteira da automação foi decidida (pré-bloqueio), mas a capacidade de pagamento/checkout fica ambígua na prática
- **Gravidade/confiança:** grave / 75.
- **Evidência:** discovery 27/08 acorda "automatizar até o pré-bloqueio; pagamento no hotel (modelo Booking)". Porém, o cliente ainda descreve casos em que "recebe direto do cliente e desconta comissão" — exceção a definir.
- **Cenário de falha:** no piloto, reservas que deveriam fechar no hotel acabam exigindo pagamento no site, ou comissões diretas entram no fluxo padrão sem regra.
- **Decisão necessária:** definir explicitamente a exceção de comissão direta e quem a autoriza.

### RV-005 — Notificação e-mail/WhatsApp ao concierge com dados do hóspede exige base legal e minimização (LGPD)
- **Gravidade/confiança:** grave / 75.
- **Evidência:** discovery 27/08 quer disparo automático de dados (nome, telefone, hotel, datas) ao concierge e dashboard; CRM de preferências existe e gera apetite de uso posterior.
- **Cenário de falha:** dados pessoais espalhados por e-mail/WhatsApp/dashboard sem consentimento, acesso por papel e retenção.
- **Decisão necessária:** definir base legal, minimização, acesso por papel, retenção e responsável antes do disparo.

### RV-006 — Não há operação de exceção nem proprietário nomeado com SLA
- **Gravidade/confiança:** média-alta / 75.
- **Evidência:** discovery 27/08 reforça o papel do concierge como diferencial, mas não define dono, escala, SLA nem alçadas de exceção.
- **Cenário de falha:** automação transfere casos críticos para uma fila sem atendimento.
- **Decisão necessária:** nomear owner, cobertura, SLA e procedimento para indisponibilidade, erro, alteração e pedido especial.

### RV-007 — Risco de escopo crescer (site + dashboard + relatórios + formulário + notificação + integração)
- **Gravidade/confiança:** média-alta / 100.
- **Evidência:** discovery 27/08 agrega reestruturação do site no Skip, área restrita, dashboard, relatórios mensais, notificação, formulário opcional e CRM (adiado). Kickoff restringia a um processo.
- **Cenário de falha:** quatro meses se fragmentam entre site, gestão e integração, e não provam o gargalo de resposta.
- **Decisão necessária:** ordenar por fase 1 com valor visível no gargalo; manter CRM e itens opcionais como evolução.

### RV-008 — Confiança de marca premium exige transparência de fonte/validade e fallback humano
- **Gravidade/confiança:** média / 75.
- **Evidência:** histórico de preço/disponibilidade errados; discovery 27/08 quer resposta (quase) imediata via Omni; formulário opcional sem IA.
- **Cenário de falha:** resposta automática inexata reduz confiança e acelera evasão para OTA.
- **Decisão necessária:** aprovar exibição de validade/origem e fallback humano.

## Pontos sólidos
- A discovery 27/08 fechou decisões estruturais importantes: site no Skip, fronteira no pré-bloqueio, pagamento no hotel, notificação ao concierge, formulário opcional sem IA, comissão como exceção, CRM adiado.
- Processo prioritário (reservas de unidades habitacionais) e métrica de dor (48h → imediato) foram reafirmados.
- Há data e dono para a prova da Omni (reunião OmniBiz 28/08) e call de implementação (31/08).

## Riscos residuais
- Sem resposta técnica OmniBiz, baseline e mapa completo, esta revisão sustenta decisão de escopo — não implementação.
- Cobertura de hotéis/inventário e política comercial da Omni.
- Pagamento, confirmação, alteração, cancelamento, reembolso e suporte pós-reserva.
- Migração de dados/volume do site atual no Skip.
- Razão social (Verde Serra vs Circuito Elegante) ainda a confirmar.