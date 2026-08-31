# Direções Fundamentadas — Circuito Elegante (v2 — 27/08/2026)

**Disparo de regeneração:** escopo base atualizado (v2) com a reunião de discovery de 27/08 (site no Skip, integração Omni, fronteira no pré-bloqueio, dashboard, notificação) — direções anteriores de 26/08 ficaram obsoletas neste conjunto de inputs.

## Eixos e candidatas

### Eixo A — Sequência de valor versus dependência da Omni
| Direção | Hipótese e ganho | Custo/risco | Confirmação necessária | Ranking |
|---|---|---|---|---|
| D1. Prova técnica/contratual da Omni primeiro | Validar capacidades (pesquisa, disponibilidade, **pré-bloqueio**), tempos de resposta e hotéis cobertos antes de prometer automação; evita repetir o fracasso de preço/disponibilidade de 1,5 ano. | Posterga interface visível; depende do fornecedor. | Reunião OmniBiz 28/08, docs, sandbox, credenciais, contrato. | 1 |
| D2. Concierge assistido com resposta humana | Captura estruturada + fila/SLA gera valor operacional enquanto a integração é provada. | Não atinge "imediato" em todos os casos. | Dono, horários e alçadas. | 2 |
| D3. Motor autônomo com pré-bloqueio automático | Fronteira **escolhida na reunião 27/08**: automação até o pré-bloqueio via Omni; checkout/pagamento permanece no hotel (modelo Booking). | Depende de a Omni efetivamente suportar pré-bloqueio via API; se não, volta para D2. | Resposta OmniBiz sobre pré-bloqueio e tempos. | Condicional, priorizado |

### Eixo B — O que a primeira versão deve concluir
| Direção | Hipótese e ganho | Custo/risco | Confirmação necessária | Ranking |
|---|---|---|---|---|
| D4. Site reconstruído no Skip com banco próprio | Reestruturar o site inteiro (Skip) com catálogo de hotéis e dados migrados; toda a operação no mesmo ambiente. | Migração/volume de dados e layout; esforço extra na 1ª entrega. | Inventário de páginas/dados do site atual e capacidade de migração. | 1 |
| D5. Área restrita/dashboard por hotel | Time adiciona hotéis, vê vagas, ocupação, agendamentos e campanhas; base para cobrança mensal. | Superfície de gestão cresce; risco de escopo. | Métricas mínimas e responsáveis definidos. | 2 |
| D6. Formulário opcional de contexto (sem IA) | Captura motivo/evento da viagem para personalizar o pós-reserva, sem custo de IA. | Dados opcionais; definir quais e como usar. | Definição do formulário (campos opcionais) e política. | 2 |

### Eixo C — Confiança, notificação e personalização
| Direção | Hipótese e ganho | Custo/risco | Confirmação necessária | Ranking |
|---|---|---|---|---|
| D7. Notificação e-mail+WhatsApp ao concierge a cada reserva | Diferencial de concierge (clientes têm a quem recorrer); time age rápido no pós-reserva. | Dados do hóspede disparados a terceiros (even interno); LGPD/consentimento; risco de volume. | Base legal, minimização e aceite do hóspede. | 1 |
| D8. Relatórios mensais por hotel para cobrança | Faturamento mensal por hotel baseado nas reservas. | Exige consistência de dados e regra de comissão. | Regra de comissão/exceção definida. | 2 |
| D9. CRM de preferências desde a 1ª entrega | Personalização total (pantufa, vinho, revista). | **Decidido adiar** (reunião 27/08): seria 2º projeto; risco de sobrecarregar a 1ª entrega e privacidade. | — | Rejeitada agora |
| D10. Comissão direta do cliente como fluxo padrão | Receber direto com desconto de comissão. | **Decidido como exceção** (reunião 27/08): manter manual/específico, não automatizar agora. | Regra de quando aplicar a exceção. | Rejeitada como padrão |

## Rejeições explícitas
- Checkout/self-checkout no site com pagamento (ex.: Stripe) na 1ª entrega — **adiado**: pagamento permanece no hotel (modelo Booking); só entra se a fronteira mudar.
- IA conversacional para captura de contexto — **substituída por formulário opcional** (decisão do consultor, aceita na reunião).
- CRM de personalização completo na 1ª entrega — **adiado para 2º projeto** (decisão da reunião).
- Comissão direta do cliente como fluxo padrão — **mantida como exceção** (decisão da reunião).
- Integrar preferências de hóspedes com hotéis agora — não demonstra necessidade para o gargalo e amplia risco de privacidade.
- Automatizar resposta sem fonte de verdade — contraria o problema histórico de preços/disponibilidade errados.
- Reconstruir motor/channel manager próprio — fora do objetivo e inviável sem inventário licenciado.

## Recomendação não vinculante
Seguir a **fronteira acordada na reunião 27/08**: D1 (prova Omni) como gate de entrada → D4 + D5 + D6 (site no Skip, dashboard, formulário opcional) como construção visível → D7 (notificação concierge) e D8 (relatórios por hotel) como apoio à operação. A automação de **pré-bloqueio (D3)** só entra depois da confirmação técnica da OmniBiz (28/08). A decisão final é humana.