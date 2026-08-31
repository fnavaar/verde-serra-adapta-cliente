# USER — contexto operacional

## Empresa e champion
- **Empresa:** Circuito Elegante; identidade jurídica Verde Serra Central Hoteleira Ltda × marca Circuito Elegante — **[VALIDAR NA CALL DE SETUP]**.
- **Champion:** Gestor/champion operacional — **[VALIDAR NA CALL DE SETUP: nome, contato e substituto]**.
- **Aprovadores:** Consultor, CSM/cliente conforme governança, e gestores responsáveis por dados, exceções e go-live — **[VALIDAR NA CALL DE SETUP]**.

## Objetivos e processo crítico
- **Objetivo:** descoberta no site → consulta/ação de reserva no Omni → registro de evento → e-mail ao concierge → suporte/handover → exceção registrada quando houver indicação/contato direto. **[CONFIRMADO: Escopo §2]**
- **Métrica:** taxa de automatização de reservas por hotel e período. Fonte, evento de reserva concluída, baseline, fórmula e meta são pré-condições a validar; não declarar atribuição sem elas. **[CONFIRMADO: Escopo §§1,4]**
- **Processo:** hóspede usa site/Omni; concierge conduz suporte e amenities; hotel conduz check-in e pagamento. **[CONFIRMADO: Escopo §2]**

## Ferramentas e fontes de verdade
| Ferramenta/fonte | Uso | Responsável | Status de acesso |
|---|---|---|---|
| Plataforma Skip | site e área administrativa | administrador da plataforma | [VALIDAR NA CALL DE SETUP] |
| Omni/OmniBiz | disponibilidade/reserva/bloqueio comprovados | operação/hotel | contrato, credenciais e sandbox pendentes |
| Resend ou equivalente | e-mail operacional ao concierge na F2 | responsável de comunicação | provider, consentimento e rol de campos pendentes |
| Registros da plataforma | hotéis, reservas administrativas, eventos e exceções | administrador | F1 planejada |

## Preferências de trabalho
- **Comunicação:** português, direta, com estado, evidência e próximo gate.
- **Cadência:** uma task por vez; teste humano explícito antes do avanço.
- **Formato de entrega:** evidências rastreáveis, checklist e roteiro de demonstração.

## Restrições e decisões que exigem validação
- Checkout, pagamento, reembolso e conciliação não pertencem à plataforma.
- CRM de personalização, IA e WhatsApp automatizado estão fora deste ciclo.
- Dados do formulário têm finalidade operacional; retenção, base legal e reuso exigem decisão.
- Papéis/alçadas, owner/SLA de exceções, regra de comissão e fonte/meta da métrica exigem validação antes de ativação.