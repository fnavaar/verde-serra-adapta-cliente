# Fluxos encontrados

- Reunião: Adapta Native - Circuito Elegante
- Data: 2026-08-12
- Link tl;dv: https://tldv.io/app/meetings/6a7c6052d5507e0013ffdf4a
- Fonte: transcrição e metadados retornados pela API do tl;dv.

## Observação
O fluxo abaixo descreve o processo atual de atendimento e fechamento de reservas, identificando os pontos de perda de cliente.

## Processo de Reserva de Hóspedes (atual)
```mermaid
flowchart TD
    A["Cliente pesquisa hotel no site/revista do Circuito Elegante"] --> B{"Ação do Cliente"}
    B -- "Clica no botão de reserva" --> C["Redirecionado para o WhatsApp do Concierge"]
    C --> D["Concierge contata o hotel manualmente"]
    D --> E["Hotel informa disponibilidade e valores"]
    E --> F["Concierge responde ao cliente no WhatsApp"]
    F --> G{"Cliente aceita a resposta demorada?"}
    G -- "Sim" --> H["Reserva efetuada"]
    G -- "Não / Desistência" --> I["Perda de venda"]
    B -- "Abre nova aba no navegador" --> J["Acessa Booking.com ou site direto do hotel"]
    J --> K["Reserva concluída fora do Circuito Elegante"]
```
