# Análise do consultor

> Este arquivo é do consultor humano. A IA criou apenas a estrutura; não preenche concordância, discordância, escolhas ou checkpoint em nome do consultor.
> **Referência:** `analise-critica.md` v2 de 27/08/2026 (AC-001..AC-007, DH-01..DH-06).

## Resposta aos achados

### AC-001 — A integração com Omni/OmniBiz (incluindo pré-bloqueio) é uma hipótese, não uma capacidade comprovada
- **Minha leitura:** [discordo]
- **Evidência ou contexto que acrescento:** é uma capacidade comprovada.
- **Decisão para o escopo final:**[discordo]
- **Razão da decisão:** é uma capacidade comprovada.

### AC-002 — "Atendimento imediato" ainda não é métrica de aceite
- **Minha leitura:** [discordo]
- **Evidência ou contexto que acrescento:** nossa meta aqui é muito em cima da reserva automática do hóspede,  o Omini garante que ele consiga reservar o hotel e travar aquela vaga, o mesmo hotel entra em contato com o hóspede para confirmação de reserva e procedimento, ou seja o atendimento é imediato e com garantia de reserva.
- **Decisão para o escopo final:** Vamos manter a métrica de automatização seguirá como nossa métrica norte
- **Razão da decisão:**

### AC-003 — O mapa operacional de regras, exceções e dados ainda não está completo
- **Minha leitura:** [concordo parcialmente]
- **Evidência ou contexto que acrescento:** concordo que nem toda a jornada está mapeada, mas todos os pontos que estão documentados seguem corretamente o fluxo da jornada que competem a Verde Serra. Todo o trâmite entre hotel x hospede é feito pelo Omnibeez.
- **Razão da decisão:** toda a parte necessáriia para nosso fluxo foi mapeada no kickoff e na call de analise
- **Decisão para o escopo final:** organizar toda a estrutura para receber a API do OMNI e reestruturar o site

### AC-004 — A primeira entrega tem fronteira definida (pré-bloqueio), mas a exceção de comissão direta precisa de regra
- **Minha leitura:** [discordo]
- **Evidência ou contexto que acrescento:** A regra se aplic em casos específicos, quando o cliente já quer garantir sua vaga e fala diretamente com o time de concierges, mas são raríssimas excessões. cada cas pode ser anotado dentro do CRM interno sem a necessidade de criar um padrão para o site.
- **Decisão para o escopo final:** Naa área restrita para administração do site, ter essa exceção para ser assinalada dentro da área de reservas por hotel
- **Razão da decisão:** Manter a lógica sem trazer essa exceção

### AC-005 — Notificação e-mail/WhatsApp e dashboard exigem base legal e minimização
- **Minha leitura:** [discordo]
- **Evidência ou contexto que acrescento:** vamos fazer o disparo de emails toda vez que o cliente fizer reserva, esse email vai com as informações do cliente para qu eo time concierges possa entrar em contato e fazer um raport com os hóspedes
- **Decisão para o escopo final:** Vamos implementar o disparo de emails via API do Resend
- **Razão da decisão:** menor nível de complexidade e máximo resultado para essa primeira fase

### AC-006 — Exceções precisam de dono e SLA
- **Minha leitura:** [concordo]
- **Evidência ou contexto que acrescento:** Existem exceções, como a de comissão direta que precisa de dono e SLA
- **Decisão para o escopo final:** Vamos implementar a regra de comissão direta na área restrita do site
- **Razão da decisão:** Manter a lógica sem trazer essa exceção

### AC-007 — O escopo cresceu; risco de fragmentação de ciclo
- **Minha leitura:**[discordo]
- **Evidência ou contexto que acrescento:** Não concordo que o escopo tenha crescido, apenas ficou mais claro e descobrimos pontos importantes que precisavam de definição antes de avancarmos
- **Decisão para o escopo final:** Seguir a lógica atual estabelecida
- **Razão da decisão:** Evitar a fragmentação do ciclo atual

## Decisões humanas

### DH-01 — Promessa da primeira versão
- **Minha leitura:** Estruturar o site para receber a API do OMNI e reestruturar a área de reservas para receber as exceções de comissão direta
- **Escolha:** [A consulta + pré-bloqueio via Omni condicionado ]
- **Razão:** já temos uma ferramenta que faz essa reserva e funciona muito bem

### DH-02 — Definição de atendimento imediato
- **Minha leitura:** o cliente que faz a reserva pelo site já recebe um email de confirmação e o time de concierge entra em contato imediatamente para finalizar a reserva e handover de amenities
- **Escolha:** [A reserva é feita no Omni e o concierge entra em contato para finalizar a reserva e handover de amenities]
- **Razão:** já temos uma ferramenta que faz essa reserva e funciona muito bem
- **Escolha:**
- **Razão:**

### DH-03 — Fonte e permissão de inventário/tarifa (e pré-bloqueio)
- **Minha leitura:** OMNI já tem o sistema de agendamento e bloqueio de reservas.
- **Escolha:** construir a lógica aqui em cima do OMNI, como uma aba de pesquisa igual a do booking
- **Razão:** melhor UX e UI para o cliente

### DH-04 — Uso do CRM na primeira onda
- **Minha leitura:** CRM interno que vamos construir na áre restrita da plataforma
- **Escolha:** O próprio omni vai fazer o cadastro do cliente, mas precismaos ter uma área de administração para inserir os hóspedes que chegam por indicação ou contato direto, além determos relatórios de ocupação e reserva para cada hotel
- **Razão:** vamos estruturar um CRM com todas as ferramentas necessárias para a operação do hotel.

### DH-05 — Owner e SLA de exceções
- **Minha leitura:** Vamos adicionar um campo específico no CRM interno
- **Escolha:** ter a lógica de excessões dentro do CRM da plataforma
- **Razão:** manter os dados centralizados

### DH-06 — Comissão direta do cliente como fluxo
- **Minha leitura:** a comissão direta é uma exceção que ocorre em casos específicos, quando o cliente quer garantir sua vaga e fala diretamente com o time de concierges
- **Escolha:** [exceção específica]
- **Razão:** são raríssimas excessões, cada caso pode ser anotado dentro do CRM interno sem a necessidade de criar um padrão para o site.

## Novas ideias do consultor

| ID | Ideia | Evidência/hipótese | Valor esperado | Risco/custo | Levar ao escopo? |
|   ter uma plataforma IGUAL ao do Booking para reserva de hotéis| O Omni já faz isso de forma excelente, só pprecisammos ajustar a lógica do site apra que funcione como uma plataforma de visualização dos hoteis |implemneetar todos os dados dentro do sistema|levar ao escopo|

## Riscos ou pontos de vista que a análise não cobriu

-

## Mudanças que quero levar ao escopo final

| Mudança | O que substitui | Por quê | Fase afetada |
|---|---|---|---|

## Checkpoint humano

- [x] Respondi todos os IDs AC e DH obrigatórios.
- [x] Registrei discordâncias e novas evidências.
- [x] Diferenciei mudança do ciclo atual de ideia para o próximo ciclo.
- [x] Autorizo usar estes apontamentos como input de `/adapta:escopo-definitivo`.