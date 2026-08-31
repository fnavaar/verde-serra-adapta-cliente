# Sugestões de conectores e automações

**Estado:** RASCUNHO. Sugestão não confirma disponibilidade, instalação, conta conectada ou autonomia. Nenhuma conta deve ser conectada antes da call de setup e da autorização humana.

| Sugestão | Tipo | Necessidade/evidência | Dado/fonte | Permissão mínima | Consumidor | Responsável | Ativação | Risco | Alternativa | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| Skip/Skip Cloud | conector de plataforma | site e área administrativa F1; Escopo §§3,5 | conteúdo aprovado, hotéis, registros/admin | projeto autorizado; menor privilégio | assistente principal, SPECs F1 | administrador | após confirmar projeto/RBAC | alteração indevida/permissão excessiva | execução manual no projeto | recomendado — validar |
| Omni/OmniBiz | API operacional | reserva/bloqueio somente na F2; Escopo §§3–4 | disponibilidade, ação de reserva, status/validade quando fornecidos | sandbox/leitura; escrita só para operação comprovada | loop de confiabilidade e F2 | operação/hotel | após contrato, credenciais, sandbox e prova por endpoint | confirmação inventada, duplicidade, dado pessoal | fluxo humano informado | necessário para F2 — bloqueado |
| Resend/SMTP | e-mail transacional | handoff ao concierge na F2; Escopo §§3–4 | dados mínimos do evento de reserva | domínio/provider autorizado; envio apenas ao destinatário aprovado | F2; confiabilidade | responsável de comunicação | após consentimento/base legal, rol de campos, destinatário teste e prova de falha | vazamento/erro de destinatário | notificação manual e painel | recomendado — bloqueado |
| Relatório/consulta de métricas | leitura/consulta | taxa de automatização F1/F4; Escopo §§1,4–5 | evento, hotel, período, numerador/denominador | leitura somente | loop de conversão | gestor/champion | após contrato de métrica e baseline | atribuição indevida/dado incompleto | contrato/planilha versionada | necessário — validar |
| Agenda mensal de revisão | automação agendada | loops F4; Escopo §5 F4 | agregados de falhas, conversão e exceções | leitura e criação de rascunho | loops F4 | gestor/champion | gatilho mensal após F4; para em dado ausente/gate | alerta sem fonte/ação autônoma indevida | revisão manual mensal | futuro |

## Regras de automação agendada

- **Gatilho/frequência:** mensal — **[VALIDAR NA CALL DE SETUP]**.
- **Condição de parada:** dado ausente, integração com erro, credencial expirada, métrica não definida ou ação que exija decisão humana.
- **Em erro:** registrar falha e preparar rascunho de diagnóstico; não repetir escrita/ação externa automaticamente.
- **Proibido:** publicar, enviar e-mail, criar reserva, alterar comissão ou conectar credenciais por inferência.