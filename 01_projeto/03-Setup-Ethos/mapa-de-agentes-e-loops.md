# Mapa de agentes e loops

## Assistente principal

| Missão | Entradas | Saídas | Skills/capacidades | Conectores | Limites | Fases |
|---|---|---|---|---|---|---|
| Executar uma task por vez e manter evidência | task, SPEC, aceite, evidências autorizadas | estado, prova, bloqueio, roteiro de teste | leitura, execução guiada, revisão de evidência | somente conectores aprovados | não aprova gate; não publica/conecta/envia sem autorização | 1–5 |

## Agentes especializados propostos

| Agente | Missão | Entradas | Saídas | Skills | Conectores | Limites | Fase/SPEC |
|---|---|---|---|---|---|---|---|
| Revisor de segurança | revisar fronteiras de dados, permissões e falhas | SPEC, contrato de integração, prova negativa | riscos e condições de ativação | revisão de segurança | Skip/Omni/Resend só quando conectados | read-only; não instala/conecta | antes de F2/F3/F4 |
| Operador de confiabilidade | preparar relatório de falhas, fallback e recuperação | logs da plataforma/Omni | relatório e itens pendentes | análise de eventos | plataforma + Omni validados | sem reserva/alteração/autonomia decisória | F4 / LOOP-01 |
| Analista de conversão | calcular e explicar taxa de automatização por hotel/período | contrato F1 e eventos validados | relatório, inconsistências e comparação | consulta/métricas | fonte aprovada | sem meta inventada/veredito autônomo | F4 / LOOP-02 |
| Analista de saúde operacional | preparar exceções de indicação/comissão e registros sem desfecho | registros administrativos | fila e relatório | análise de exceções | plataforma aprovada | não decide comissão/alçada | F4 / LOOP-03 |

## Relação com fases

- **F1:** catálogo, acesso, registros e contrato de métrica fornecem a base; não há loop ativo.
- **F2:** Omni/e-mail só entram após as provas e aprovações declaradas.
- **F3:** dashboard, exceções e segregação de acesso fornecem a leitura operacional.
- **F4:** os três loops usam entregas existentes; não ampliam capacidades.
- **F5:** valida sistemas, conectores, agentes e loops ponta a ponta.