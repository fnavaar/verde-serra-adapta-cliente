# Requisitos do Escopo — Circuito Elegante (v2 — 27/08/2026)

Regenerado após a reunião de discovery de 27/08 e o escopo v2. IDs `RQ-NNN` reutilizados da cadeia anterior com ajustes; decisões da reunião incorporadas.

| ID | Resultado/ator | Limites e fluxo | Sinal de sucesso/evidência | Dependências e decisão |
|---|---|---|---|---|
| RQ-001 | Hóspede envia solicitação estruturada a partir do site reconstruído no Skip. | Campos mínimos: nome, telefone/e-mail, hotel/destino, check-in, check-out, hóspedes; não coletar dados desnecessários. | Solicitação chega à operação com origem; formulário validado. | Site migrado/definido; definição de canal. |
| RQ-002 | Sistema consulta disponibilidade/tarifa autorizada via Omni. | Somente leitura (se documentado); falha não vira resposta inventada; resposta deve ter origem/timestamp/validade. | Casos de teste batem com fonte; latência medida. | API/licença/sandbox Omni (prova 28/08). |
| RQ-003 | Hóspede recebe retorno imediato quando a resposta for confiável. | "Imediato" precisa de SLA/percentil; preço/validade/condições visíveis. | Tempo de resposta medido por canal. | Baseline e política comercial. |
| RQ-004 | Concierge recebe exceções com contexto. | Ambiguidade, erro, indisponibilidade e pedido especial não são automatizados sem alçada; notificação e-mail+WhatsApp ao time. | Handoff registrado e atendido no SLA. | Owner, escala, alçadas, consentimento. |
| RQ-005 | Operação direciona o hóspede para rota autorizada de compra/reserva. | **Checkout/pagamento permanece no hotel (modelo Booking)**; pré-bloqueio via Omni somente se confirmado; comissão direta é exceção específica. | Tentativas e resultado atribuíveis. | Prova técnica Omni (pré-bloqueio). |
| RQ-006 | Gestor mede performance e falhas por hotel. | Dashboard por hotel: vagas, ocupação, agendamentos, campanhas; relatórios mensais para cobrança. | Painel consistente; relatório mensal gerado. | Fontes de eventos e regra de cobrança. |
| RQ-007 | Dados do hóspede são protegidos. | Minimização; notificação e-mail+WhatsApp ao concierge e dados no dashboard exigem base legal/consentimento e acesso por papel; CRM de preferências fora da 1ª entrega. | Política/consentimento aprovados. | Negócio/jurídico e dados. |
| RQ-008 | Equipe opera e corrige o processo. | Runbook de exceções; formulário opcional de contexto (motivo/evento) capturado no fechamento; sem depender de pessoa-chave única. | Simulação de casos críticos concluída. | Champion e equipe operacional. |

**Decisões fechadas na reunião 27/08 (fatos, não inferência):** site no Skip; automação até o pré-bloqueio via Omni; checkout/pagamento no hotel (modelo Booking); área restrita/dashboard; notificação e-mail+WhatsApp; formulário opcional sem IA; comissão direta como exceção; CRM de personalização adiado.

**Decisões ainda abertas (humanas):** definição operacional de "imediato"; prova técnica/contratual do pré-bloqueio Omni (28/08); migração de dados do site atual; regra de exceção de comissão; baseline e política de cobrança; LGPD/consentimento para notificações; escopo exato do dashboard.