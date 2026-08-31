# Escopo Base — Concierge de Reservas 24h | Circuito Elegante

**Plano:** `Plano — 89c2ebd7` · **Cliente cadastrado:** Verde Serra Central Hoteleira Ltda / operação referida nas fontes como Circuito Elegante · **Data:** 2026-08-27 (v2 — consolidada reunião de discovery de 27/08) · **Status:** base para análise crítica.

## 1. Objetivo e recorte
Reduzir o tempo de retorno ao hóspede para solicitação de reserva de unidades habitacionais, hoje de até 48 horas ou mais, para retorno imediato quando a consulta puder ser atendida com dados confiáveis. O recorte é exclusivamente a jornada B2C de reserva de hotéis; não inclui a operação B2B do selo, revista, ESG nem reestruturação ampla de CRM.

O resultado de negócio pretendido é reter a intenção de compra dentro do Canal Circuito Elegante, reduzindo a saída para Booking.com, sites de hotéis ou outros canais. A fonte ainda não fornece baseline de conversão, receita vazada ou volume de consultas: estes são dados de descoberta, não premissas.

## 2. Evidências e contexto
- O DMO declara o piloto como concierge 24h conectado ao motor de reservas e objetivo de eficiência em reservas (`03-Projeto/00-DMO.md`, respostas de 18/08).
- A call de vendas descreve quase 100 estabelecimentos, o histórico de tentativa integrada que produziu uma reserva em 1,5 ano e a dependência de acesso/licença OmniBiz (`02-Reuniao/Sales Call/01-transcricao.md`, 12/08).
- O kickoff fixa o processo em unidades habitacionais e a métrica operacional como tempo de retorno, de até 48h para imediato (`02-Reuniao/Kickoff Call/02-Ata_reuniao.md`, 20/08).
- **Discovery 27/08** (Navaar + Manoela + Mônica) fecha decisões-chave: reconstruir o site no **Skip** (banco próprio), integrar **Omni** para pesquisa/disponibilidade, automatizar até o **pré-bloqueio**, manter pagamento/checkout no hotel, área restrita com dashboard por hotel, notificação e-mail+WhatsApp ao concierge, formulário opcional de contexto (sem IA), comissão direta como exceção e CRM de personalização adiado para 2º projeto (`02-Reuniao/Consultoria Call/` — artifacts/ce-reuniao-2026-08-27/).

## 3. Fluxo atual (as-is)
1. Hóspede chega via tráfego pago, parceiros, site ou revista e pesquisa hotéis.
2. Ao desejar reservar, é direcionado ao WhatsApp/e-mail do concierge.
3. Concierge consulta o hotel manualmente; recebe disponibilidade e tarifa; responde ao hóspede.
4. O retorno pode levar 48h ou mais. Enquanto espera, o hóspede pode abrir Booking.com ou site do hotel e concluir fora do canal.
5. Há dados históricos de preferências em CRM, porém seu uso nesta jornada não está validado.
6. Quando aceita, o time realiza pré-bloqueio (autorização de débito no cartão) e repassa ao hotel; o pagamento final é feito **no hotel** (no check-in), com variação de parcelamento por hotel. Se o hóspede não comparecer, o hotel debita ao menos uma diária.

## 4. Fluxo-alvo (ASA) — modelo Booking, validado na discovery de 27/08
1. Hóspede informa destino, datas, hóspedes e critérios mínimos em uma interface/canal autorizado.
2. O sistema consulta fonte autorizada de inventário/tarifa (**Omni**) e devolve opções apenas quando a resposta for íntegra e atual.
3. O hóspede demonstra interesse / faz pré-agendamento (pré-reserva), **sem pagamento no site**.
4. **Omni executa o pré-bloqueio** automaticamente (fronteira da automação).
5. O hóspede recebe a reserva **por e-mail** (garantida) — modelo Booking; no check-in, o hotel finaliza o pagamento (cartão).
6. O time da Circuito Elegante é **notificado** (e-mail + WhatsApp) a cada reserva e o concierge entra em contato para suporte e ofertas (diferencial de concierge).
7. Exceções — inventário indisponível, ambiguidade, erro de integração, solicitação especial ou política comercial — são encaminhadas ao concierge humano com contexto.
8. Eventos de consulta, resposta, handoff, tentativa de reserva e conclusão são registrados para medir velocidade, funil e falhas.

## 5. Capacidades no escopo, condicionadas à descoberta
- **Reconstrução do site no Skip** (banco próprio) com todas as informações, replicando e melhorando o layout atual, integrado ao mesmo ambiente.
- **Área restrita/admin** (só responsáveis): adicionar/editar hotéis e informações; migrar dados do site atual.
- **Dashboard por hotel**: total de vagas, taxa de ocupação, histórico de agendamentos e campanhas.
- **Integração de leitura com a Omni** (pesquisa/disponibilidade + pré-bloqueio); autenticação, endpoints, tarifas, inventário e limites são desconhecidos.
- **Notificação automática** (e-mail + painel) a cada reserva e disparo de contato WhatsApp pelo concierge.
- **Formulário opcional de contexto** (motivo/evento da viagem) no fechamento da reserva — **sem IA**; obrigatórios apenas os dados exigidos pelo hotel.
- **Relatórios mensais por hotel** para cobrança das reservas.
- Fila de exceções e handoff para concierge humano; trilha de auditoria de respostas.
- Painel operacional mínimo para tempo de resposta, taxa de resposta automática, handoffs, erro de consulta e conversão atribuível.
- Recuperação de abandono é evolução candidata, não escopo comprometido, até existir consentimento, dados de identificação e baseline.

## 6. Fora de escopo nesta etapa
- **Checkout/self-checkout no site** (ex.: Stripe) — mantido no hotel na 1ª entrega (modelo Booking); só entra se o cliente mudar a fronteira da automação.
- **CRM de personalização completo** (perfil do hóspede: pantufa, vinho, revista, preferências) e atualização cadastral pós-reserva — **2º projeto/momento**.
- **IA conversacional** para captura de contexto — substituída por formulário opcional.
- Substituir OmniBiz, construir novo channel manager/motor próprio ou agregar inventário de hotéis sem fonte licenciada.
- Precificação própria, alteração de tarifa, emissão/cobrança/pagamento, cancelamento ou mudança de reserva sem regras e autorização explícitas.
- Expor CRM de preferências aos hotéis, campanhas de marketing, portal B2B, revista, selo e ESG.
- Prometer disponibilidade, preço ou confirmação sem fonte transacional validada.

## 7. Regras, dados e riscos
- **Comissão direta do cliente** (recebimento direto com desconto de comissão) é tratada como **exceção específica**, não fluxo padrão.
- Respostas comerciais devem trazer origem/timestamp de consulta, validade e política de fallback; o sistema não pode inventar preço ou disponibilidade.
- Dados de hóspedes e preferências são potencialmente pessoais/sensíveis ao contexto de hospitalidade. Base legal, minimização, retenção, acesso e responsabilidade devem ser definidos antes do uso.
- A licença/acesso à Omni foi mencionada, mas não há prova de API, escopo de dados, capacidade de pré-bloqueio/criação de reservas nem permissão de redistribuição.
- O histórico de uma integração anterior com falhas de preço/disponibilidade exige validação por casos de teste antes de qualquer exposição ao hóspede.
- A latência de resposta da Omni interfere diretamente na experiência do usuário; precisa ser medida.
- Não sobrecarregar a 1ª entrega: CRM de personalização deve ficar separado para o sistema de agendamento funcionar bem.

## 8. Lacunas obrigatórias para fase de especificação
1. **Prova técnica e contratual da Omni**: documentação (não pública), sandbox, credenciais, read/write, capacidade de **pré-bloqueio automático**, rate limits, hotéis cobertos, política de revenda e tempo de resposta — responsável: cliente + OmniBiz (reunião 28/08) + consultor.
2. Vídeo/processo detalhado atual e desejado, incluindo canais, campos, regras e exceções — responsável: Manoela/equipe.
3. Definição de "atendimento imediato", janela de medição e baseline por canal — responsável: champion e operação.
4. Dono operacional, alçadas e SLA de exceções; confirmação de Mônica/Manoela e papel do concierge — responsável: cliente.
5. Jornada de compra, pagamento, confirmação, cancelamento, LGPD e atribuição — responsável: negócio/jurídico/operação.
6. Escopo exato do dashboard (métricas e campanhas) e do formulário opcional de contexto — responsável: cliente + consultor (call de implementação 31/08).

## 9. Próximos passos acordados (27/08)
1. **Reunião OmniBiz** — 28/08 às 11h; consultor envia perguntas (API, tempo de resposta, capacidade de pré-bloqueio) para a cliente fazer ao fornecedor.
2. **Call de implementação** — segunda 31/08, 10:45–12:00, com Manoela e Mônica (aguardando e-mail da Mônica para convite).
3. **Não gerar SPECs/tasks** antes das respostas da OmniBiz e do fechamento do escopo.

## 10. Autoavaliação
- **Grounding 4/5:** fontes rastreáveis; capacidade da API não foi assumida.
- **Completude 4/5:** as-is, ASA (modelo Booking) e fronteiras de automação fechadas na discovery; falta prova da Omni e baseline.
- **Clareza 4/5:** objetivo, fronteiras e fora de escopo explícitos.
- **Acionabilidade 3/5:** adequada para análise e descoberta, não para implementar.
- **Concisão 4/5:** foco mantido no gargalo acordado.